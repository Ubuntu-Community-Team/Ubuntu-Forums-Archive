---
title: "javascript install from web page"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by JJBrodkorb on 2007-12-28
I don't know if this is the correct forum to ask this, but I'll try here first.
I have an ssl vpn at work that I would like to connect to but the javascript install won't work because it says that I have to have root permissions for the install.  The ssl vpn is a netgear ssl312 vpn box.  I checked my user and added the administration permissions, in fact I added all permissions, but it still won't install.  Does anyone have any ideas on how I can get this to install?  The only way I can find to start the install is from the web page, so I can't do it through a terminal session.

Thanks for any help you can give.
Jim

---

### Post by taurus on 2007-12-28
Why don't you start firefox with root privilege.  Then, you don't have to worry about permissions to write to outside of your own $HOME directory.

Applications -> Accessories -> Terminal
```
gksudo firefox
```

---

