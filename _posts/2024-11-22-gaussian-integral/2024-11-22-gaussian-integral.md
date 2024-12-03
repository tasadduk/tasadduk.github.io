---
layout: post
title:  "Evaluating the Gaussian integral"
---

**Problem:** prove the following:

$$ \int_{-\infty}^{\infty} e^{-x^2} \, dx = \sqrt{\pi}.$$

This is the famous Gaussian integral, which is also known as the Poisson integral. Three things fascinate me about this integral. One, you cannot find an elementary function $$ f(x) $$ such that $$ f(x) = \int e^{-x^2} \, dx.$$ Two, the improper integral $$ \int_{-\infty}^{\infty} e^{-x^2} \, dx $$ is equal to $$ \sqrt{\pi} $$, which we prove below. And finally, there are several different methods of proving this statement. Below, we share couple of ways of deriving this identity.

## Polar coordinates
The polar coordinates method is probably the most popular one, usually introduced in a calculus course.

Define the following:

$$ 
\begin{align}
I(a) &:= \int_{-a}^a e^{-x^2} \, dx, \quad \text{where } a>0. \nonumber \\
I &:= I(\infty) = \lim_{a \to \infty} I(a) = \int_{-\infty}^{\infty} e^{-x^2} \, dx
\end{align}
$$

We are interested in evaluating $$ I $$, or $$ I(\infty) $$. Note that

$$
\begin{align}
I^2(a) &= I \cdot I \nonumber \\
&= \left(\int_{-a}^a e^{-x^2} \, dx\right)\left(\int_{-a}^a e^{-y^2} \, dy\right) \nonumber \\
&= \int_{-a}^a \int_{-a}^a e^{-(x^2+y^2)} \, dx \, dy. \label{eq:double_integral_rectangle}
\end{align}
$$

One can see that $$ I^2(a) $$ is a double integral over the square region $$ S(a) = [-a,a] \times [-a, a] $$.

Denote $$ D(a) $$ to be the disk of radius $$ a > 0 $$ centered at the origion. Then, geometrically, the disk $$ D(a) $$ is inscribed in the square $$ S(a) $$, and the disk $$ D(\sqrt{2}a) $$ lies outside outside $$ S(a) $$, interecting all four vertices.

Let

$$ J(a) = \iint_{D(a)} e^{-(x^2+y^2)} \, dx \, dy $$

Since $$ e^{-(x^2+y^2)} $$ is always positive, and 

$$
\text{area}\{D(a)\} < \text{area}\{S(a)\} < \text{area}\{D(\sqrt{2} a)\},
$$

we can say that 

$$ J(a) < I^2(a) < J(\sqrt{2}a) \label{eq:inequality}.$$

Changing into polar coordinates with $$ x = r \cos \theta, y = r \sin \theta $$, we get 

$$
\begin{align}
J(a) &= \iint_{D(a)} e^{-(x^2+y^2)} \, dx \, dy \nonumber \\
&= \int_0^{2\pi} \int_0^a r e^{-r^2} \, dr d\theta \nonumber \\
&= \pi (1 - e^{-a^2}).
\end{align}
$$

And so $$ J(\sqrt{2} a) = \pi (1 - e^{-2 a^2}) $$. Taking limits, we have $$ \lim_{a \to \infty} J(a) = \pi (1 - e^{-a^2}) = \pi. $$ Also, $$ \lim_{a \to \infty} J(\sqrt{2} a) = \pi. $$ Then, by applying the squeeze theorem to inequality \eqref{eq:inequality} we have $$ \lim_{a \to \infty} I^2(a) = I^2 = \pi. $$ Therefore, $$ \sqrt{\pi} = I =  \int_{-\infty}^{\infty} e^{-x^2} \, dx. $$ 



## Change of variables
This method is due to Laplace, according to Wikipedia [^wiki]. 
Let $$ I = \int_{-\infty}^{\infty} e^{-x^2} \, dx. $$ By the evenness property, one can write 

$$ I = 2 \int_0^{\infty} e^{-x^2} \, dx. $$

Next, we apply this trick to write $$ I^2 $$ as a double integral. The variable of integration $$ x $$ can be replaced with any other symbol, so we get

$$ I = 2 \int_0^{\infty} e^{-x^2} \, dx = 2 \int_0^{\infty} e^{-y^2} \, dy, $$

and consequently,

$$
\begin{align}
I^2 &= I \cdot I \nonumber \\
&= \left(2 \int_0^{\infty} e^{-x^2}\right) \left(2 \int_0^{\infty} e^{-y^2} \, dy\right) \nonumber \\
&= 4 \int_0^{\infty}\int_0^{\infty} e^{-(x^2+y^2)} \, dy \, dx.
\end{align}
$$

Introduce a new variable $$ t $$ so that $$ y = x t $$ and $$ dy = x \, dt $$. Using this substitution and changing the order of integrations, we get

$$ I^2 = 4 \int_0^{\infty}\int_0^{\infty} x e ^{-x^2(1+t^2)} \, dx \, dt. $$

Note that

$$
\int_0^{\infty} x e ^{-x^2(1+t^2)} \, dx = -\left.\frac{e^{-x^2(1+t^2)}}{2(1+t^2)}\right|_0^{\infty}
= \frac{1}{2} \frac{1}{1+t^2}.
$$

Using this in the last equation for $$ I^2 $$, we get

$$
\begin{align}
I^2 &= 4 \int_0^{\infty} \frac{1}{2} \frac{1}{1+t^2} \, dt \nonumber \\
&= 2 \, \left. \arctan t \right|_0^{\infty} \nonumber \\
&= \pi.
\end{align}
$$

Thus, we have shown that $$ I^2 = \pi $$. Hence, 

$$ I = \int_{-\infty}^{\infty} e^{-x^2} \, dx = \sqrt{\pi} \nonumber.$$





## Bibliography
[^wiki]: [Wikipedia: Gaussian Integral](https://en.wikipedia.org/wiki/Gaussian_integral#cite_note-york.ac.uk-3)
