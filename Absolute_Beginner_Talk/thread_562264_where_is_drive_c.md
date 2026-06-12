---
title: "where is drive c"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by tonycl1669 on 2007-09-28
Hi sorry a newbie here...
I have just installed Ubuntu 1.4
Installed wine
Then installed Microsoft Office

But how the devil do I run office?
Please help me!!!!!

---

### Post by dpar on 2007-09-28
[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)

---

### Post by ryanVickers on 2007-09-28
I would just use OpenOffice, but if you must...

look in your home directory, then add /.wine/drive_c/Program Files and you should see it :)

---

### Post by dn_desaku on 2007-09-28
What version of Office did you install?
It should be in Applications > Wine then it should be staright forward. 

If it is not there, bust out the Terminal

Note: if you just  navigate to your home folder looking for .wine you won't be able to find it. Ya gatta run Nautilus with admin rights.

```
sudo nautilus
```
enter your passoword 
and then navigate to your Home folder

goto .wine> drive_c > then you should be able to find it from that point on.

If that does not work, screenshots help :)

Also, Ubuntu comes with OpenOffice.org already so I would not see a purpose to install MS Office (unless you like its interface better and it feels better to you) 

I get chills running MS Word and Oo Writer together side by side. I get the same chills running Photoshop and GIMP side by side :lolflag:

---

### Post by bruce89 on 2007-09-28
> **tonycl1669 said:**
> 
I have just installed Ubuntu 1.4
!

1.4? What on earth is that? 6.04 I assume.

---

### Post by ryanVickers on 2007-09-28
Yea, I was going to ask that too, but... :)

---

### Post by dn_desaku on 2007-09-28
1.4? Whoa. That's so old...or so new or both!

This poor fellow must've been experiencing shock from the greatness of Tux :lolflag:

[QUOTE=tonycl1669]Hi sorry a newbie here...[/QUOTE]

Don't apologize for asking for help. We all need help at some time or another. :)

---

### Post by Kilz on 2007-09-28
> **dn_desaku said:**
> 

If it is not there, bust out the Terminal

Note: if you just  navigate to your home folder looking for .wine you won't be able to find it. Ya gatta run Nautilus with admin rights.

```
sudo nautilus
```
enter your passoword 
and then navigate to your Home folder



There are better ways of doing this. First of all its best to use gksudo if you want to start a gui application in administration mode. Secondl, you dont need to be an admin to look at hidden folders. In nautilus (non admin) click Go, then location. The address bar will show. Then type in the location ```
~/.wine
``` to view the hidden wine folder.

---

### Post by ryanVickers on 2007-09-28
> Note: if you just navigate to your home folder looking for .wine you won't be able to find it. Ya gatta run Nautilus with admin rights.

That's preposterous!  You can type in /home/you/.wine and go in it, or just turn on "show hidden files", or... :lolflag:

---

### Post by dn_desaku on 2007-09-28
> **ryanVickers said:**
> That's preposterous!  You can type in /home/you/.wine and go in it, or just turn on "show hidden files", or... :lolflag:

Whoa, I didn't know that. :( That would save me so much time. Thanks for saying so.

---

### Post by ryanVickers on 2007-09-28
Thought that was pretty obvious, but ok then, your welcome! :p

It is *your* home folder, so *you* have full rights to it :)
You would only need root privilages if your vooking at root owned folders/files with other groups set as "no access".  You can even view the root home folder with**out** root privileges, you just can't change anything :)

---

### Post by por100pre1 on 2007-09-28
To see hidden files just press CTRL+H. BTW, if you ever need Nautilus with superuser privileges use gksudo nautilus instead.

---

### Post by handydan918 on 2007-09-28
> **dn_desaku said:**
> Whoa, I didn't know that. :( That would save me so much time. Thanks for saying so.

yeah, man. If it's in your /home and you can't open it, you don't own it. Be afraid....

---

