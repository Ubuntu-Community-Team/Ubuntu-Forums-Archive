---
title: "how to connect to work file space"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by col_b on 2006-11-07
Hello,

I've just installed 6.10.  All went smoothly :) 

I use linux in work, but used windows xp at home.  I used putty to connect to my filespace in work (i.e a dedicated IP address).  That was all very easy.

I now need to connect to my linux filespace at work using my new ubuntu system.  I've searched the forums here, but everything is a bit confusing. ](*,) 

Can anyone suggest how I connect to my filespace at work?  I guess I don't install putty.  Is there another program that I can use?

Thankyou all very much in advance.

Col

---

### Post by Bachstelze on 2006-11-07
Hi and welcome to Ubuntu :)

You're not giving much info here, what kind of "filespace" is it ? NFS, Samba, FTP ?

---

### Post by col_b on 2006-11-07
Thanks for the quick reply.

I'm not sure what kind of file space it is :???: ....

I just used putty, put in the IP address, selected port 22, enabled X11 forwarding, and it connected right up.  it asked me for my username and password and I was in...

Sorry I can't be of much more help.... :???:

col_b

---

### Post by Bachstelze on 2006-11-07
All right, port 22, it's SSH then. Just type *ssh username@host* in a terminal, it will give you a command line. I don't know how to use X for this, have a look at the manpage or wait for someone else :)

---

### Post by col_b on 2006-11-07
Ok, thanks!  I'll give it a go. :) 

Col

---

### Post by col_b on 2006-11-07
HymnToLife, thanks for your help.  That has worked.

Cheers! :) :) :)

---

