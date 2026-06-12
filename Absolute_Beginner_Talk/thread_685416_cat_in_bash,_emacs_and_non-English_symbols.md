---
title: "cat in bash, emacs and non-English symbols"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by evillan on 2008-02-02
When I use the terminal (bash) to display a text-file with "cat name.txt", which I've written and/or edited in emacs, all the non-English symbols like å, æ and ø are replaced with a question mark instead.

I do not have this problem with text flies written in other text editors like nano, gedit or OpenOffice. So it's probably an emacs-ocentric problem.

Solutions? Ideas? Help?

---

### Post by mali2297 on 2008-02-02
> **evillan said:**
> When I use the terminal (bash) to display a text-file with "cat name.txt", which I've written and/or edited in emacs, all the non-English symbols like å, æ and ø are replaced with a question mark instead.

I do not have this problem with text flies written in other text editors like nano, gedit or OpenOffice. So it's probably an emacs-ocentric problem.

Solutions? Ideas? Help?

Check that you use UTF-8 in emacs. 

Here is the content of my **~/.emacs** file if it can help:
```

(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(auto-compression-mode t nil (jka-compr))
 '(auto-save-default nil)
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "latin-1-prefix")
 '(global-font-lock-mode t nil (font-lock))
 '(inhibit-splash-screen t)
 '(load-home-init-file t t)
 '(tool-bar-mode nil))

;; Manually set variables
(set-input-mode nil nil 1)

```

---

### Post by evillan on 2008-02-02
> **mali2297 said:**
> Check that you use UTF-8 in emacs. 

Here is the content of my **~/.emacs** file if it can help:
```

(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(auto-compression-mode t nil (jka-compr))
 '(auto-save-default nil)
 '(case-fold-search t)
 '(current-language-environment "UTF-8")
 '(default-input-method "latin-1-prefix")
 '(global-font-lock-mode t nil (font-lock))
 '(inhibit-splash-screen t)
 '(load-home-init-file t t)
 '(tool-bar-mode nil))

;; Manually set variables
(set-input-mode nil nil 1)

```

That doesn't do it for me. 

This is a test text file edited in emacs
```
døtte ær en tåst
```

And this is in the terminal
```

name@name:~$ cat test3.txt 
d&#65533;tte &#65533;r en t&#65533;st

```

---

### Post by mali2297 on 2008-02-02
Upload the sample text file as an attachment.

---

### Post by evillan on 2008-02-02
> **mali2297 said:**
> Upload the sample text file as an attachment.

Done

---

### Post by mali2297 on 2008-02-02
> **evillan said:**
> Done

I can read that file with any application (except for less).

Post the output of
```

locale

```

---

### Post by evillan on 2008-02-02
> **mali2297 said:**
> I can read that file with any application (except for less).

Post the output of
```

locale

```
Okay, locale outputs
```
LANG=en_DK.UTF-8
LC_CTYPE="en_DK.UTF-8"
LC_NUMERIC="en_DK.UTF-8"
LC_TIME="en_DK.UTF-8"
LC_COLLATE="en_DK.UTF-8"
LC_MONETARY="en_DK.UTF-8"
LC_MESSAGES="en_DK.UTF-8"
LC_PAPER="en_DK.UTF-8"
LC_NAME="en_DK.UTF-8"
LC_ADDRESS="en_DK.UTF-8"
LC_TELEPHONE="en_DK.UTF-8"
LC_MEASUREMENT="en_DK.UTF-8"
LC_IDENTIFICATION="en_DK.UTF-8"
LC_ALL=

```

---

### Post by mali2297 on 2008-02-05
Alright, I checked your file with
```

name@name:~$ file test3.txt                                                                                                                              
test3.txt: ISO-8859 text

```
This means that you still don't use UTF-8 in Emacs. The output should have been
```

test3.txt: UTF-8 Unicode text

```
which is what I get if I write the same thing in Emacs.

Did you try with an exact copy of my ~/.emacs file?

---

