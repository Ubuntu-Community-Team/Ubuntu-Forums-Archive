---
title: "Question about removing Ubuntu :("
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by emma.meg on 2006-09-10
I have been using Ubuntu for a few days now and do like it, but after returning to college, I realized that there are just too many things not working with what I need for school. So here's the problem, I have an IBM Thinkpad which is most likely out of warranty and that I did a clean installation of Ubuntu on. So, basically, there are no traces of Windows on here but I'm going to try and sort that out with Lenovo.

My main issue is this:

I no longer have a storage device to save my files too. How do I create a new partition to put all those files so that when I do the install of Windows where the files are remains untouched? Is that even possible?

Thanks.

---

### Post by David Corrales on 2006-09-10
I'd boot the dapper livecd and use the application Gparted to repartition your disk the way you want to in a graphical way.

---

### Post by edrodgers731 on 2006-09-10
You could probably boot with the CD, format your swap partition to ext3 and copy your files over there.  Then, install windows over the / partition.  I assume you have a swap partition separate from your / partition..

-Ed

Sorry.. You will need to format swap as fat32 so that windows can read it as well...

Other options.. Use an external USB disk, or a USB key.

Just curious... What exactly DOESN'T work in Ubuntu?

-Ed

---

### Post by Mimsy on 2006-09-10
My college's intranet and the online classes won't work, because they demand IE, along with weird Windows stuff that I don't quite understand. (Which is frustrating to me, since I considermyself fluent in Windows.) I tried getting to the pages using IE in Wine, but that wouldn't work either. So I do the campus computer labs, or borrow my SO's computer. He has to have Windows for work.

/Mimsy

---

### Post by edrodgers731 on 2006-09-10
That's a bummer.  I'm sure there is a way to make IE in linux do the trick, but I know what you mean.  My university did the same thing to me.  I'm glad that's over!

Good luck!

-Ed

---

### Post by jensenhearing on 2006-09-15
Have you tried using "virtual machine" in Linux? You can have a windows XP running on the virtual machine.

The two programs that can do that is the VMware and the QEMU. Once you've got that installed you can allocate "disk space" to your virtual machines as well as RAM etc. In that way you may not even have to use WINE.

---

### Post by mcmillanje on 2006-09-15
have you tried using the opera web browser? it has an option to 'identify as ie' where it tells (i think) the server it's ie.
(but i actually have no idea if it'd work)

you could also dual boot... it's got it's problems but i think you could run ie (from your windows install partition) from wine and keep ubuntu if you wanted it.

or, you could use a webserver to move your files over (upload, reformat-reinstall, dload)

sorry you don't like ubuntu... I did just what you're doing with suse before i found ubuntu.

---

### Post by tagra123 on 2006-09-15
Have you tried installing vmplayer. I leave it running all day long and use both XP and Xubuntu on the laptop and XP and UBUNTU on the desktop. Works great for me. No problems so far anyway.

---

