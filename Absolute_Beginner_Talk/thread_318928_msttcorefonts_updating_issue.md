---
title: "msttcorefonts updating issue"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by tacoweapon on 2006-12-14
When I run an update of any kind I always end up getting this error output.  Is there a way to stop this from coming up?  I'm running Dapper desktop.

Thanks.


E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

---

### Post by linear on 2006-12-14
Sounds like you have a (bad) proxy set for wget. Look for this in /etc/wgetrc and/or ~/.wgetrc. If you _are_ behind a proxy server, fix the address; if not, turn off the proxy. Some more info is [here]("http://ubuntuforums.org/showpost.php?p=541276&postcount=1006").

---

