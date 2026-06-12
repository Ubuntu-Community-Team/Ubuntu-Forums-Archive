---
title: "network shares with vista"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by galinha on 2007-08-13
Hello :

I see that there are ither users with with the same problem.

I have 3 vista box in my house all in the same workgroup.
I had instaled umbutu 7.04 in another that i want to use as a media center.

From the umbutu box i can see the vista boxs , see the files ...BUT I CANT COPY OR USE THEM....

I had instaled Konqueror and is the same....

Im a toial newbie in linux ....is there a easy solution to solve this...

Thnks a Lot.

Luis.

---

### Post by jambarama on 2007-08-13
> **galinha said:**
> Hello :

I see that there are ither users with with the same problem.

I have 3 vista box in my house all in the same workgroup.
I had instaled umbutu 7.04 in another that i want to use as a media center.

From the umbutu box i can see the vista boxs , see the files ...BUT I CANT COPY OR USE THEM....

I had instaled Konqueror and is the same....

Im a toial newbie in linux ....is there a easy solution to solve this...

Thnks a Lot.

Luis.

To make sure I understand, you installed Ubuntu successfully, and you can find the network shares (Windows network shares are sometimes called "samba" shares), you can view the files, but you can't copy them locally, or open them.  

If this is the case it sounds like a permissions issue--meaning the way the system is accessing the files it doesn't believe it has read/write privileges.  This could be caused by permissions on the Vista boxes themselves, but it sounds like the shares are read/write between Vista boxes, so that probably isn't the issue.  

What you'll want to do is to "mount" the samba share(s) to your file system.  [This tutorial ]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently")worked great for me personally, it is very "step by step".  Give that a try.  

If you'd rather not fiddle with this stuff, I've had pretty good luck getting read/write access when using smb4k.  If you open the package manager, find smb4k, install it, and use it (you may have to run it as root, meaning once installed simply type "sudo smb4k" into a terminal, then input your password--but try smb4k without the sudo first), you may have better luck.  

The tutiorial two paragraphs up is sure fire in my experience, but either way, let us know how it works out.

---

