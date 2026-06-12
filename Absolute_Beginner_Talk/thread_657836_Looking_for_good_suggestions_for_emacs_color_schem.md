---
title: "Looking for good suggestions for emacs color scheme for programming"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2008-01-04
I will soon be in a Fortran programming class where I'm expecting to spend a significant portion of time in front of an editor, in my case emacs most likely.  I have an old .emacs color scheme that someone gave me, but I was wondering if you could suggest any other color schemes or recommend improvements to this one.  

In the past, I've just sort of gone with what I already had or what was provided (a couple of college classes forced us to use M$ products to write code), but if I could get some color advice (or maybe even some .emacs file segments) from some veteran coders, I would appreciate it.

Here is the color segment of the file I'm currently using:

```


(set-face-foreground 'region "black")
(set-face-background 'highlight "CadetBlue")
(set-face-background 'secondary-selection "MediumSeaGreen") 

(custom-set-faces
'(default ((t (:foreground "Wheat" :background "DarkSlateGray"))))
'(list-mode-item-selected ((t (:background "gray68"))) t)
'(font-lock-comment-face ((t (:foreground "Coral"))))
'(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
'(font-lock-string-face ((t (:foreground "LimeGreen"))))
'(font-lock-keyword-face ((t (:foreground "aquamarine"))))
'(show-paren-mismatch-face ((((class color)) (:foreground "white" :background "red"))))
'(isearch ((t (:foreground "black" :background "paleturquoise"))) t)
'(paren-match ((t (:background "darkseagreen4"))) t)
'(widget-field-face ((((class grayscale color) (background light)) (:background "DarkBlue"))))
'(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))) t)
'(font-lock-type-face ((t (:foreground "#9290ff"))))
'(highlight ((t (:foreground "black" :background "darkseagreen2"))))
'(show-paren-match-face ((((class color)) (:foreground "black" :background "yellow"))))
'(font-lock-variable-name-face ((t (:foreground "Khaki"))))
'(font-lock-doc-string-face ((t (:foreground "green2"))) t)
'(font-lock-function-name-face ((t (:foreground "deepskyblue1")))))


```

---

### Post by twin_57103 on 2008-01-09
I just finished a Java class and I tried to use emacs, but always ended up using gedit - just couldn't get the hang of emacs.  The default color schemes are different - it can be configured to a color scheme files, although I have never tried.  If you haven't tried it, maybe check it out?

---

