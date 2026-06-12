---
title: "fontconfig scanning error &amp; ttf-opensymbol"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by jazzman83 on 2007-03-29
Hello, I just got on my computer this morning and noticed there were some update so I routinely installed them as is normal.

Upon setting them up the computer told me there were problems with the ttf-opensymbol package and that fontconfig is having scanning errors.  Now everytime I try to install a package I get this error.  I cannot remove ttf-opensymbol or reinstall it.

```
Preparing to replace ttf-opensymbol 2.0.4-0ubuntu5 (using .../ttf-opensymbol_2.0.4-0ubuntu5_all.deb) ...
Unpacking replacement ttf-opensymbol ...
Setting up ttf-opensymbol (2.0.4-0ubuntu5) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 ttf-opensymbol
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ttf-opensymbol (2.0.4-0ubuntu5) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 ttf-opensymbol

```

Any help would be great.

---

### Post by macross3003 on 2007-03-29
already posted, try:
[http://www.ubuntuforums.org/showthread.php?t=326341&highlight=ttf-opensymbol](http://www.ubuntuforums.org/showthread.php?t=326341&highlight=ttf-opensymbol)

---

