---
title: "Other pcs on my network can see my ubuntu pc, but can't access
its shared drives"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by richardyates on 2006-11-23
Last week, whilst doing an automatic update, Windows XP finally gave me
the excuse to abandon windows and move my remaining box to Linux.

I now have a network on which there are 3 Macs running OS X and a PC
running Ubuntu 6.06.  Its running under samba, because that's how I learned networking when all my machines ran windows, and also because one of the macs dual boots to xp when I need it to.

My demented fumblings with linux in the past have obviously stood me in
good stead, because my old windows HDD appears on the Ubuntu desktop and I
can browse its files and even open them:-)

But I want to go further and be able to get at those files from my other
networked machines, and this is where I have hit a problem.

I have installed Samba and my Ubuntu PC can be seen by the other machines
on the network, but the problem comes when I try to open the old HDD
(Inventively called "Advent" by Advent computers), or indeed, even my
Ubuntu user (inventively called "richard" by me), both of which are
supposedly shared.

If I try to do this using  Places|Network Servers on my ubuntu box, then a
dialog appears saying "authentication required"  It then asks for my
username (which it fills in as "richard"), my domain (pre-filled in as
WORKGROUP) and my password.  If I enter my password and click connect, it
comes straight back with the same dialog box.

Having looked at this a bit, my domain, being a legacy windows network is
called "MSHOME", but changing the domain to that and putting in my other
details makes no odds.  I think my windows username might have been
"richardyates", trying that doesn't help either, so I just can't work out
how to log in.  Its amusing on the Ubuntu box that I can just open the HDD
"Advent" with no trouble whilst I can't going through network servers, but
on my macs its very frustrating - I can see all the shares I want to
connect to, but in the absence of the correct username and password can't
connect to them (OK that's fair enough, but not helpful when you don't
seem to be able to get the right combination).

On the mac, when I try to log in, it tells me my domain is MSHOME, my
username is RICHARDYATES, but then rejects any password I put in.  I think
I've tried every possible combination of upper and lower case, so I'd
really appreciate some help.

One extra bit of info.  The drive called advent was originally my C: drive and is thus hda1, formatted NTFS.  The permissions on this drive tell me that the owner is root and that I can't change those permissions because I'm not the owner, but I can't find out how to change that.

So in short my other machines can see all my shared drives, but can't authenticate onto them.  I'm as certain as can be my passowrds and usernames are correct, and my other machines can all see each other and access each others' drives

I'm stuck, and I really need some help - please assume I know almost nothing and you won't go far wrong.  I had it recommended to me elsewhere that I should use command sudo chmod 777 /media/had1.  It appeared to spend quite a long time changing permnissions, but it seems nothing happened and it certainly hasn't fixed the problem:-(

I *really* want to get past this, so here's hoping

---

### Post by hardyn on 2006-11-25
i would also like to know, tried to do the same with a friends macbook, could not figure out how to log in.

---

### Post by richardyates on 2006-11-25
Glad I'm not the only one, surely someone can help?

Since I posted this I've also tried to see the ubuntu machine from the mac over NFS,  the mac can't even see the drives then, let alone access them:-(

---

