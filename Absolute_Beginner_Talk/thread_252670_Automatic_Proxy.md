---
title: "Automatic Proxy"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Haggis on 2006-09-07
My network uses an automatic proxy URL.  This is fine in Firefox, but I cannot get it to work in Gaim.  The same problem was discussed here:

[http://www.ubuntuforums.org/archive/index.php/t-191064.html](http://www.ubuntuforums.org/archive/index.php/t-191064.html)

however the solution offered only works when running bash.  It was to type

sudo gedit /etc/bash.bashrc

Add at end of file :

export http_proxy=http://proxyname:port
export ftp_proxy=http://proxname:port

However, I run csh not bash.  My naive attempt - just typing the above into /etc/csh.cshrc - didn't work.  What's the csh equivalent?

---

### Post by Apple 101 on 2006-09-07
It should work with GAIM.  You should use the 'Global settings' to configure GAIM.

---

### Post by Haggis on 2006-09-07
Do you mean 'Global Settings' within GAIM?  Under Preferences->Network, I selected 'Use environmental Settings' from the Proxy menu, but this still gave me a proxy error message.

---

### Post by Haggis on 2006-09-07
I have now found the 'global settings' I think you were referring to.  I have put in the correct automatic proxy info and still to no avail.

By default I actually use xubuntu - I can't find anywhere to put in proxy information in its general menus, only IP info.

---

