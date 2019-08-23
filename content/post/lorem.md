---
title: "Lorem ipsum dolor sit amet"
date: 2018-09-30T15:17:27-07:00
draft: true
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam in euismod arcu.
Nulla facilisi. Donec vel nisi sem. Phasellus congue convallis luctus. Ut non
enim eget velit vehicula aliquet. Pellentesque condimentum facilisis pharetra.
Nulla ac sollicitudin justo, vitae euismod velit. Nullam lobortis elementum
neque, sit amet accumsan augue vehicula et. Nullam convallis arcu sit amet
magna commodo, id finibus neque placerat. Quisque id tincidunt leo, a pretium
magna. Ut maximus nisl sed leo tincidunt imperdiet. Maecenas consectetur ante
tellus, ac bibendum mauris vulputate at. Praesent efficitur dictum bibendum.
Vestibulum porttitor sem ut imperdiet sollicitudin.

Source code
===========

Curabitur ultricies metus nisl, vitae egestas nisl mollis non. Cras at libero
mattis, bibendum est vitae, sagittis dolor. Aliquam cursus, est sed eleifend
rhoncus, est eros dapibus justo, vel imperdiet mi nulla sit amet dui. Cras
efficitur aliquam tincidunt. Nulla consequat ipsum quis diam consequat iaculis
. In venenatis at neque ut sodales. Sed a auctor est. Suspendisse aliquam
accumsan nunc. Nulla accumsan venenatis risus, in fermentum nunc tincidunt
vitae. In et neque ut est mattis cursus. Quisque sed diam non ex iaculis
commodo. Vestibulum risus leo, luctus in mollis ac, mattis ac mauris. Morbi
sit amet orci convallis, convallis ante vitae, mollis elit. In hac habitasse
platea dictumst. Curabitur sed dui est. Ut imperdiet, diam id suscipit aliquet
, erat dolor tempor sem, a accumsan orci libero vitae tellus.

{{< highlight go >}}
func (h highlighters) chromaHighlight(code, lang, optsStr string) (string, error) {
	opts, err := h.cs.parsePygmentsOpts(optsStr)
	if err != nil {
		jww.ERROR.Print(err.Error())
		return code, err
	}

	style, found := opts["style"]
	if !found || style == "" {
		style = "friendly"
	}

	f, err := h.cs.chromaFormatterFromOptions(opts)
	if err != nil {
		jww.ERROR.Print(err.Error())
		return code, err
	}

	b := bp.GetBuffer()
	defer bp.PutBuffer(b)

	// Added debug
	fmt.Printf("[%s] input to Chroma = `%s'\n", lang, code)
	
	err = chromaHighlight(b, code, lang, style, f)
	if err != nil {
		jww.ERROR.Print(err.Error())
		return code, err
	}

	// Added debug
	fmt.Printf("output from Chroma = `%s'\n\n", b.String())

	return h.injectCodeTag(`<div class="highlight">`+b.String()+"</div>", lang), nil
}

{{< / highlight >}}

Integer tempus eget lorem a dapibus. Phasellus tempor justo id urna sodales
eleifend. Pellentesque et justo sed est elementum vestibulum ac ac nulla.
Mauris molestie neque in rutrum vehicula. Lorem ipsum dolor sit amet,
consectetur adipiscing elit. Integer tempor pulvinar velit et lacinia. Morbi
blandit orci risus, vitae iaculis magna cursus ac. Nunc eget sagittis tellus.
Donec sed molestie enim. Interdum et malesuada fames ac ante ipsum primis in
faucibus. Donec id dui ac turpis finibus faucibus non feugiat ante.


Showing LaTeX
=============

In et molestie augue, sit amet pellentesque velit. Sed ornare gravida nunc
consectetur semper. Fusce gravida nibh vel sapien vehicula, sit amet imperdiet
erat pharetra. Nam a dignissim neque. Donec facilisis vehicula lacus id
tincidunt. Praesent consectetur felis in ligula eleifend vehicula. Donec
semper velit et dui porta tristique. Proin eget eleifend mauris. Etiam sit
amet pulvinar enim. Cras auctor mattis sem, a faucibus leo. Phasellus ut
sapien hendrerit, vestibulum sem ac, porta risus. Praesent metus ante,
ullamcorper id est quis, vestibulum tempor felis. Morbi vel ipsum dictum massa
porta pulvinar vitae blandit diam.

Here is inline math: $\sqrt{3x-1}+(1+x)^2$.

<p>$$
\left( \sum_{k=1}^n a_k b_k \right)^{2} \leq
 \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$</p>

<p>$$
\mathbf{V}_1 \times \mathbf{V}_2 =
   \begin{vmatrix}
    \mathbf{i} &amp; \mathbf{j} &amp; \mathbf{k} \newline
    \frac{\partial X}{\partial u} &amp; \frac{\partial Y}{\partial u} &amp; 0 \newline
    \frac{\partial X}{\partial v} &amp; \frac{\partial Y}{\partial v} &amp; 0 \newline
   \end{vmatrix}
$$</p>

<p>$$
\frac{1}{(\sqrt{\phi \sqrt{5}}-\phi) e^{\frac25 \pi}} =
     1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
      {1+\frac{e^{-8\pi}} {1+\ldots} } } }
$$</p>

<p>$$
1 +  \frac{q^2}{(1-q)}+\frac{q^6}{(1-q)(1-q^2)}+\cdots =
    \prod_{j=0}^{\infty}\frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
     \quad\quad \text{for $|q|&lt;1$}.
$$</p>

<p>$$
\begin{align}
  \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &amp; = \frac{4\pi}{c}\vec{\mathbf{j}} \newline
  \nabla \cdot \vec{\mathbf{E}} &amp; = 4 \pi \rho \newline
  \nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} &amp; = \vec{\mathbf{0}} \newline
  \nabla \cdot \vec{\mathbf{B}} &amp; = 0
\end{align}
$$</p>

<p>$$
\begin{equation}
x(t) = e^{\int_{t_0}^tp(s)ds}\Bigg(\int_{t_0}^t\Big(q(s)e^{-\int_{t_0}^sp(\tau)d\tau}\Big)ds + x_0\Bigg).
\end{equation}
$$</p>

Donec convallis magna eu metus vestibulum, id tincidunt mi ornare. Quisque
eget urna ut tellus iaculis lacinia tincidunt non mauris. Maecenas est eros,
molestie a ligula non, vehicula iaculis nibh. Pellentesque aliquet vehicula
magna nec ultricies. Aliquam semper vulputate nisi, ut ullamcorper sapien
condimentum sit amet. Praesent aliquam condimentum ultrices. Donec suscipit
tortor eu lectus dapibus imperdiet. Ut vehicula ornare lorem quis laoreet.
Nullam quam diam, tincidunt non justo eget, ultrices fermentum augue. Ut
luctus condimentum maximus. Sed eu dictum lacus. Etiam ut metus eget ante
scelerisque tincidunt ac a erat. Mauris at mollis risus. Proin mollis eros non
urna convallis, eu euismod justo blandit.
