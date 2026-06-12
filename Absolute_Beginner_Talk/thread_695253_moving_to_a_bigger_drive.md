---
title: "moving to a bigger drive"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2008-02-12
I have ubuntu installed on a 80gig drive in my server, and I'd like to move my music from the 300 gig drive in my desktop over to the server, so the whole system ends up on the 300 gig drive.

So what I'm thinking to do is: back up all the music elsewhere, copy the installation from the 80 gig to the 300 gig, then remove the 80 gig all together and then copy over whatever music and whatnot.

I'm just wondering if that would work and how I'd want to do it.  I was thinking I'd use "dd" but I suspect I might need to change a couple things after I do that and I'm not exactly sure what (also note, the 80 is an IDE drive, the 300 is sata)

If anyone knows more about this kind of operation let me know.

---

### Post by dcstar on 2008-02-12
> **Hospadar said:**
> I have ubuntu installed on a 80gig drive in my server, and I'd like to move my music from the 300 gig drive in my desktop over to the server, so the whole system ends up on the 300 gig drive.

So what I'm thinking to do is: back up all the music elsewhere, copy the installation from the 80 gig to the 300 gig, then remove the 80 gig all together and then copy over whatever music and whatnot.

I'm just wondering if that would work and how I'd want to do it.  I was thinking I'd use "dd" but I suspect I might need to change a couple things after I do that and I'm not exactly sure what (also note, the 80 is an IDE drive, the 300 is sata)

If anyone knows more about this kind of operation let me know.

Gparted will do partition copies.

---

### Post by oedha on 2008-02-12
what if......i'll do this
1. backup your files
2. backup /var/cache/apt/archives 
3. back up you conf files
4. clean install on 300gig
5. put everything back to 300
6. 80gig.......slave maybe or ???

---

### Post by Hospadar on 2008-02-13
Well I want use the 80 in my desktop machine, hence why the server will have only the 300.  I would just do a clean install except I have some stuff set up that was a little tricky that I'd rather not have to redo (WebDAV calendar, a few other things)

If I use gparted to copy the partitions, I assume I have to re-set up grub? how exactly do I go about that

---

### Post by click4851 on 2008-02-13
I've had luck with the Super Grub live disc, for restoring grub.

---

