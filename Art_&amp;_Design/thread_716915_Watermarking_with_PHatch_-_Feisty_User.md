---
title: "Watermarking with PHatch - Feisty User"
date: 2008-03-06
forum: Art &amp; Design
---

### Post by Kat of Zion on 2008-03-06
In my Windoze days, I used to use a program called PictureShark which was a tool that one could use to mass watermark graphical images.  From what I can see, this company has not come up with any type of *nix based version of thier program.

Looks like PHatch might be the equilivant but they do not seem to have a download for Fiesty.  Is this program too new for someone who is sticking to Feisty? If that is the case, anyone know of another graphical program that does watermarks?

---

### Post by stani on 2008-03-06
Hi,
The Ubuntu installer works as well on Feisty, although only Gutsy is mentioned. 
Don' t worry,
Stani

---

### Post by Kat of Zion on 2008-03-06
I tried to install the one linked in the download section, titled Gutsy.  However, I got the following errors when attempting to install this debian with gdebi.
[B]
Your system has broken dependencies.  this application cannot continue until it is fixed. To fix it, run 'sudo synaptic' or 'sudo apt-get install -f' in a terminal window.[/B]

I did run 'sudo apt-get install -f' and tried to install phatch with gdebi once more.  Looks like that was what fixed it.  Strange that my synaptic didnt put its indicator up regarding the updates that I received.

Kat

---

### Post by Reverendspam on 2008-03-13
Try this:

1) sudo apt-get install python python-wxgtk2.8 python-imaging

2) download this file and save to your desktop or wherever you want:

[http://sd-2986.dedibox.fr/photobatch/download/package/phatch_0.1.bzr492-1_all.deb](http://sd-2986.dedibox.fr/photobatch/download/package/phatch_0.1.bzr492-1_all.deb)

3) Click on file to install

It works for me. Good Luck

-joe

---

