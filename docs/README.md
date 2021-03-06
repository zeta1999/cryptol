Programming Cryptol README

To use the check-exercises tool, invoke via `cabal v2-exec
check-exercises --`. This requires the path to the LaTeX file to be
checked, and has options to specify paths to the cryptol executable
and log directories.

To annotate LaTeX files for the `check-exercises` program, we use the
following commands:

* `\begin{replinVerb}` and `\end{replinVerb}`

  This is the markup equivalent of the `Verbatim` environment.
  However, it has the added effect of adding every line of the block
  to a list of commands to be issued to the cryptol REPL.
  
* `\replin{...}`

  Inline equivalent of `replinVerb` environment. Markup equivalent of
  `\texttt{...}`.

* `\hidereplin{..}`

  Like `\replin{...}`, but is not rendered at all by LaTeX. This is
  for issuing "hidden" input to the REPL that will affect the output
  (like `:set base=10`, for example), but which we don't want to
  include in the PDF.

* `begin{reploutVerb}` and `\end{reploutVerb}`

  This is the markup equivalent of the `Verbatim` environment.
  However, it has the added effect of adding every line of the block
  to the expected output of the preceding `\replin` commands. If we add
  a `replinVerb` environment or inline `\replin` command after a
  `reploutVerb` environment, it has the effect of "completing" the
  previous input/output pair to issue to the repl. See CrashCourse.tex
  for examples.
  
* \replout{...}`

  Inline equivalent of `reploutVerb` environment. Markup equivalent of
  `\texttt{...}`.

* `\hidereplout{..}`

  Like `\replout{...}`, but is not rendered at all by LaTeX. This is
  for recording "hidden" output from the REPL that we don't want to
  include in the PDF.
  
* `\restartrepl`

  This has the effect of terminating the previous input/output REPL
  pair without having to include a `reploutVerb` environment or
  `\replout` command. When we don't record any expected output, the
  actual REPL output is not checked, but is instead simply issued to
  the REPL to ensure no errors are raised.
