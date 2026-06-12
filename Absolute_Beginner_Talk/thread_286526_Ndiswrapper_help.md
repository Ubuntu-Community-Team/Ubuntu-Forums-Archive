---
title: "Ndiswrapper help"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by blairellis on 2006-10-27
<-- Noob, so bear with me here 

OS is Ubuntu 6.06

I need to install a network card driver and I need some help.

I had Mandriva One and that was a sinch to use, it had a selection for the ndiswrapper right in the configuration. However, after installing Ubuntu, it recognizes the card while in the networking area along with the ethernet port, but it is not working and connecting to the net. (Im dual booting in XP in case your wondering how Im posting here.)

My card is a Xterasys XN-2524G and I have the CD with the driver .inf file here.

Went to terminal.
cd /media/cdrom/driver/ <-- That worked
sudo mdiswrapper -i tnet1130.inf <-- I got an error message of: "sudo: ndiswrapper: command not found"

So, I am assuming I have to install ndiswrapper. I downloaded this file: "ndiswrapper-1.27.tar.gz" found here [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Again, I am a noob, so Im looking for a little help here. Im a little fuzzy on the directions on how to actually install it. All the terminal commands are VERY new to me.

Once I get that installed, I think I can manage to get the ndiswrapper working and the driver installed.

Thanks again!

---

### Post by ReaderRat on 2006-10-27
You mispelled ndiswrapper
> udo mdiswrapper -i tnet1130.inf <-- I got an error message of: "sudo: ndiswrapper: command not found"

---

### Post by blairellis on 2006-10-27
it wasnt a copy/paste

good eyes I didnt even see it ;)

---

### Post by blairellis on 2006-10-27
ok, driver is installed, but I still cant get it to connect to the router downstairs. what the heck?!

---

