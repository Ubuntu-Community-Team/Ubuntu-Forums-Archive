---
title: "trying to install sound card"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-08
o boy this one taking me forever,but tring to install using this guide ttp://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide
in step# 4 it tells you to

# Type this into the shell sudo nano /etc/modules
# Add only the name of the module to be loaded at the end of the file. In my case, the via82xx module gave me sound so I added "snd-via82xx" to the end of the file.(iii) Make sure that you have all channels unmuted in alsamixer.
 so in sudo nano /etc/modules i have added my sound card at the end snd-sbawe
but how do you save this setting tried the commands at the bottom of this screen but keep putting text into my last line,also is that the correct line to input my sbawe sound card.

 thanks again all you all must be getting sick of me posting about my sound card problems](*,) ](*,) ](*,) but it's been 3 days trying to get it going:-? :-?

---

### Post by broekskw on 2006-12-08
hi again sorry but in a terminal i check to see if the  command alsamixer works but keep getting this error

helpppppppppppppppppppppppp:-# :-? ](*,) :???:

---

### Post by Adramelech on 2006-12-08
^ means Ctrl key so:

Make your changes, then Ctrl+x to exit, it will ask you if you want to save the changes or not.

---

### Post by broekskw on 2006-12-08
thanks, did you have a chance to look at my setup to see if that was correct:D

---

### Post by broekskw on 2006-12-08
ok i think it's time to blow up this sound card.i did everything in that guide in my other post.first command showed nothing  aplay -l
second command showed everything but a sound card lspci -v
so then i did this

#

    *
          o If your soundcard is not onboard, make sure that it is properly seated in the PCI slot. If your card is working under Windows then this is not a problem. 

# Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

then did this

Now go back to the shell and type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]. For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx.

and got all of this ???? have no clue as to what all this says see screen shot
so then i did this

Success

    * A success here means that your soundcard was installed, but it was not being loaded. Now you have loaded it for the current session.
    * To load it for all sessions (you will probably want to do this) you will have to edit /etc/modules (I think this is the file, I'll check once I get to my Dapper PC).
    * Type this into the shell sudo nano /etc/modules
    * Add only the name of the module to be loaded at the end of the file. In my case, the via82xx module gave me sound so I added "snd-via82xx" to the end of the file.(iii) Make sure that you have all channels unmuted in alsamixer. 

typed in terminal sudo nano /etc/modules and added bellow the last line  snd-sbawe and saved it i think, then i typed alsamixer in terminal to make sure all was not nuted but it keeps telling me that

alsamixer: function snd_ctl_open failed for default: No such device
broeks@broeks-desktop:~$

so now comes out the dynamite :sad:

---

### Post by Anolis on 2006-12-11
I was just curious why you post whole screenshots of your desktop to show error messages when you can just copy and paste? :P

---

### Post by broekskw on 2006-12-11
sorry about that next time will cut and past:mrgreen:

---

### Post by j002 on 2006-12-11
There is a soundcard installation guide "on-board" your harddrive.

Go to "help" then "excerpt from Ubuntu book *something*".

It's quite far down the list.

You do a modprobe and then if its says nothing (if its the wrong driver it should say something like "failed to install").

Then run  alsamixer and move the bars with TAB and the cursor keys.

then you gedit and type snd-whatever in the file (its like autoexec.bat) and save it.  This is not explained in the book excerpt.

You have to re-start the computer for it to take effect.

---

