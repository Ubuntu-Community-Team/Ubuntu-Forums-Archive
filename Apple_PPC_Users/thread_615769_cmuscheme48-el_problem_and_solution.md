---
title: "cmuscheme48-el problem and solution"
date: 2007-11-17
forum: Apple PPC Users
---

### Post by dnichols on 2007-11-17
I had a problem with cmuscheme48-el, solved it, and wanted to share the solution.  Installing with cmuscheme48-el with synaptic produced an error message during configuration but would then show up as installed.    Although installed, it wouldn't work, and in addition, anything that depended on cmuscheme.el (which comes with emacs) wouldn't work either.

The problem turned out to be that package cmucl-source was needed but never showed up as a dependency.  After installing cmucl-scheme, cmuscheme48-el reinstalled without an error message, and now works great.

I also had to add the following to my .emacs file:

(require 'cmuscheme48)
(setq scheme-program-name "mzscheme")
(autoload 'run-scheme
  "cmuscheme48"
  "Run an inferior scheme process."
  t)

As you can see, I'm using mzscheme, but cmucl-scheme had to be present to get everything working.

---

### Post by dnichols on 2007-11-17
That should be  (require 'cmuscheme48 )   (without the space between the 8 and the right paren)
instead of the icon.

By the way, I'm using emacs22.  I don't think I had this problem until I switched from emacs21 to 22.

---

