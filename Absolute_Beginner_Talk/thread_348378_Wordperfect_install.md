---
title: "Wordperfect install"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by frankiethepill on 2007-01-28
Newbie trying Ubuntu again- more success this time around as it is making more sense now- but I have been trying to install Wordperfect for Linux I got on a disc some years ago- most of my windows based docs are in wordperfect format. In a terminal, going to cdrom as ROOT user the book tells me to type   ' ./install.wp ' which should start the installer- it won't work=
listing of directory

root@francis-desktop:/media/cdrom0# ls
clipart   install.wp   manual    README.txt            sdk
fontlist  KDE_Red_Hat  netscape  Registration_Key.txt  shared
fonts     linux        readme    remove.wp             YMTRANS.TBL

results:-

root@francis-desktop:/media/cdrom0# ./install.wp
-bash: ./install.wp: /bin/sh: bad interpreter: Permission denied

What am I doing wrong?

Also- what is the correct pronounciation for 'Linux'- is the 'i' as in 'pin' or as in 'pine' ?

TIA Francis

---

### Post by dwblas on 2007-01-28
OpenOffice and KWord both read and write Wordperfect formats.  I don't know about Abiword or any Gnome base word processor.  So, you don't have to jump through any hoops here to access Wordperfect docs.

---

### Post by irish_flu on 2007-01-28
Sorry, I'm too much of a newb myself to help you install your Wordperfect.  That said, I can concur with the other poster that Open Office will read and write your WP documents (and should do fine even if you're sharing with other WP users).

I can also tell you that most English-speaking folks say "linux" with the "i" as in "pin".  The originator of the Linux kernel, Linus Torvalds, is from Finland and is a native Swedish speaker.  In Swedish, his name would not be "pronounced "Lie-nus", but rather "Lee-nus".  I suppose that, based on that, You could say "Lee-nux" to refer to the kernel and still be cool.  :)

---

### Post by Myglaren on 2007-01-28
There does not appear to be an option in Abiword to save as a WordPerfect document.

---

### Post by irish_flu on 2007-01-28
Hmmmm I take back what I said, I can't find a way to save documents as Wordperfect in Open Office.

---

### Post by WiseElben on 2007-01-28
This might help: [http://linuxmafia.com/wpfaq/downloadwp8.html#DOWNLOADURL](http://linuxmafia.com/wpfaq/downloadwp8.html#DOWNLOADURL)

---

### Post by frankiethepill on 2007-01-29
Thank you for your replies- I've tried the OpenOffice solution but it doesn't work properly with some of my slightly more complicated files (anything with a text box basically) though it will read simple plaintext. I'll have a try with the linuxmafia suggestions and see how it goes.
Regards, Francis

---

### Post by editrix on 2007-02-08
> **frankiethepill said:**
> Thank you for your replies- I've tried the OpenOffice solution but it doesn't work properly ...

I think you'll find that none of the Linux word processors "work properly." None can, for example, search/replace codes, let alone reveal codes. For we WP lovers, it's what keeps us in Windows.

Please, please, if you do manage to get WP running, let us know how, and how it compares to the Win version. You'll be doing many of us a service.

---

### Post by Crayoneater on 2007-02-08
you might need to remove dash....so you could type: sudo apt-get remove dash
and if it doesn't fix anything, you can just reinstall dash: sudo apt-get install dash
dash seems to mess up some shell scripts i think, i'm no expert though

---

