---
title: "Making a boot drive"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by snwbrder0721 on 2007-10-19
Ok, so I'd like to install ubuntu on an external hard drive and then be able to take that drive and pop it in an old machine and boot it up. The HD is completely formatted (ntfs).

I've been trying to load the ubuntu installer on my new machine (xp)  but so far no luck. When I put in the CD (which I verified the data on) it does the splash, then does some install and asks for a reboot. On reboot it goes to an ubuntu screen, I select "install ubuntu" and it starts what I call the loading screen (ubuntu logo and loading bar going back and forth), but hangs up after about 3 minutes (I've waited it out for about 10 with no progress shown). What can I do to get this past this? Once I get past this can I even install ubuntu on the external drive? Any help is appreciated!!!

---

### Post by Pierre Lourens on 2007-10-19
First, what is your system? You may have downloaded the wrong CD, but that's unlikely.  It is also possible that your disc is damaged or wasn't burned correctly.  Do you get to [[COLOR="Blue"]this [/COLOR]]("http://assets.lifehacker.com/assets/resources/2007/10/11.php")screen?  If so, try: Check CD for Defects.

If anything fishy comes up, just try reburning the ISO on a new disc.  Hopefully you'll have better results.

If the CD isn't the problem, I don't necessarily know.

---

### Post by Pierre Lourens on 2007-10-19
Additionally, did you eject the CD after installing and before the complete reboot?  Normally, when Gutsy shuts down, it asks you to eject the CD then press enter; it then completely shuts down. Did that happen with your computer?

---

### Post by snwbrder0721 on 2007-10-19
I did get to the screen you linked to. I choose the top option, install and it hung up on the next screen (what I referred to as the loading screen). I didn't eject the disk, it didn't mention anything about that.

my system is an HP running Windows XP home, sp2, 2 gb ram, 160 gb HD, intel 3 ghz

Thanks for the help!

---

### Post by Pierre Lourens on 2007-10-19
So, is the problem fixed?

This is the typical process:
[LIST=1]
[*]Put in disc
[*]reboot to ubuntu, the screen you got where you choose to install
[*]ubuntu loads up the desktop, user chooses "install" on the desktop screen
[*]user selects options, selects partition stuff, installs
[*]computer asks to be rebooted
[*]user ejects CD as computer shuts down
[*]ubuntu should run after reboot
[/LIST]

Are you saying you don't have anything after Step 2, or you didn't do step 6 as shutting down?

---

### Post by snwbrder0721 on 2007-10-19
Ok, I think windows was interfering with the live cd loading. I downloaded the alternate ubuntu, burnt to disc and managed to install it... almost.

The install went OK, but then it froze up on the restart and trying to load in a similar spot to what I was getting earlier with the live cd (which makes me further suspect windows conflicts). So I said forget it, and pulled the HD since technically the install was complete. I popped it in the machine I want to run it on (dell 733mhz, 384 ram) it booted to the HD then hangs up on the boot up screen where it says "Running local boot scripts (/etc/rc.local) [OK]" so I guess whatever the next line is, that's whats hanging it up? I still haven't actually seen ubuntu load completely at this point. Any ideas on how to solve this? Keep in mind this is my first foray into linux so detailed instructions are appreciated.

---

### Post by Matuku on 2007-10-19
This may seem a retarded question (and I'm sorry if it offends your intelligence) but I read your posts as if you were trying to load the Live CD whilst still within Windows XP; is this the case or is it just me?

---

### Post by snwbrder0721 on 2007-10-19
I finally got everything figured out and ubuntu booted up completely!!! In the end my video card (nvidia geforce 5500) caused the error I described above on my dell. 
Thanks to everyone for their help!

---

### Post by Pierre Lourens on 2007-10-19
Congratulations!  I'm glad that it worked out for you.  Enjoy your fresh Ubuntu install!  Cheers..

---

