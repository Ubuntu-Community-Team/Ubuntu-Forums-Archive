---
title: "Terminal print out when trying to run K3B"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by grewolf on 2007-10-02
Can someone tell me what this means please 

I tried to copy and paste the read out from the terminal screen and I received an error from the forum so will attach it as a office doc.  If someone can tell me how to copy and paste it here I will do that if preferred 

Here is the error from the forum that I received

[COLOR="Red"]You have included 54 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
[/COLOR]


If anyone could help me.  I don't even know where to begin forum searches for this or google.

---

### Post by ofb on 2007-10-03
I'll guess that you tried to post it directly, rather than within the code tags.

Hence various items like colons and brackets were turned to 'smiles', and put you over the image limit per post.

Try again, and this time select the # sign from the forum editor tool bar. That will give you the 'code' tags to post between.

---

### Post by eph1973 on 2007-10-03
Are you talking about the BadDevice messages?  Those are probably from your xorg.conf file, because of the stylus, pen, and eraser drivers that get loaded up, and then xorg can't find them whenever an X-type program starts up.  If that's what you are referring to, it's easy enough to fix with some quick comments in your /etc/X11/xorg.conf file.  If that's not what you are referring to, what part of all that are you concerned about?

---

