---
title: "DVD &amp;CD Problems"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-07-23
Some months ago, if I put a CD or DVD in my Linux(Breezey)machine, an icon would pop up on the Desk top and clicking on it made it work. Now I have a Dapper CD, but cannot get it to work. If I need to treat it like a live CD and have it start at boot, then thats the problem, as I cannot find out how to get CD or DVD to boot first.Can someone please help.
Thanks in advance..............Sarum.

---

### Post by orb9220 on 2006-07-23
You must boot with the cd by going into your bios and making the cd/dvd the first boot device in your boot sequence,

The live CD works by booting up from startup then you can check out ubuntu desktop and apps and check it out. If you want to install then you double click the install icon. Before that tho I highly recommend that all person's read up on the install steps and procedure before actually doing it.

Good Luck

---

### Post by blu-monkey on 2006-07-23
To get into BIOS, press delete when you turn your computer on and it shows the numbers flashing on the screen,I think it's the memory test or something (Del, not backspace). Sometimes it might be an Fnumber key but it should say when you turn the computer on....oh and turn the screen on first so you can see it all.

---

### Post by sarum on 2006-07-24
Thanks both of you for your replies. Before delving into the BIOS I've clicked Places/Computer/then right click on CD-ROM1 (I've tried CD-ROM2 as well). Then a left on 'Mount Volume' and the reply is.......'Unable to mount selected volume'
         'Mount: special device /dev/hdd does not exist'
Is there something here that should be put right. If I click on 'eject' that works.

Since starting this letter I've tried BIOS. Press esc on start up. Its more complicated than the other OS(ME), and if anyone can point me to an FAQ dealing with order of start up I be grateful. Other comments also welcome, thanks in advance...Sarum.

---

### Post by orb9220 on 2006-07-24
Well first if you have your motherboard manual thier should be a chapter on the bios settings.

If not then when you enter the bios use the arrows keys to navigate the menus 
at the top. down and up arrows will take you into a paticular menu left and right will take you across the menu's esc key will take you out to start.

You need to find a menu that says boot order or anything that looks close to that on mine its a menu at the top I right arrow to it then down arrow to get it settings for that menu.

In a boot order menu you should see 1st boot device,2nd boot device,etc
first boot device should be cdrom

below those is devices if I arrow down to them and hilight the cdroms and hit enter a popup shows 2 cdroms which i use the arrow to select my nec cdrom device and hit enter.  Now I know I have cdrom as 1st boot device and that it is the nec drive. Now I hit escape and arrow over to settings and down arrow to save settings and reboot.

And Done.

---

### Post by sarum on 2006-07-24
Hi Orb:,I don't have the mobo manual. I bought the machine 2nd hand for Linux learning. So single boot to Ubuntu Breezey. On boot-up, if I press 'Esc' early enough I get a dialog offering 3 choices. I press 'e' to edit the 1st choice and I get a list. Last on the list is 'boot' which I think is what I need. I can arrow down and 'e' again. Then I get terminal - not sure if thats what it's called. It's here that I don't know what to type. I have used CLI and have lists of commands, but no luck. I have often altered the BIOS on my other computer to try out live cds, Ubuntu seems very different; and I'm not complaining about it. I'm just eager to learn.

  I'm still mystified as to why, when I click on CDROM1 & CDROM2 icons on my panel, I am told that they can not be mounted because = "special device: /dev/hdc(or hdd) does not exist".
  Thanks for your help. Looking forward to hearing from you or any others who may be able to help..........Sarum

---

### Post by orb9220 on 2006-07-24
No that is the grub menu you have to enter your bios before that. On boot up you should see a press #### button to enter setup or bios message you will only have a second or two to enter the key press. Mine is the del key.

It could be esc,del or a function key. Watch the screen closely it should show what key to hit to enter bios.

---

### Post by sarum on 2006-07-24
Yes thanks orb:, esc.del did it. I've had a quick go with it. 'Advanced' on my other machine altered the disc start. There's a 'boot' heading that shows CDROM as first boot. I'll mess about with it this evening. Thanks again for your help..Sarum

---

### Post by sarum on 2006-07-25
Hi, I've tried various things in the BIOS. Its really only under the 'boot' heading that I find boot sequence, and that already has 'First =ATAPI CDROM'.
I have also tried a music CD and started CD Player and got the following.
"/dev/cdrom is not pointing to a valid CD device. It may be because
a/   CD support not present
b/   you don't have permission
c/   /dev/cdrom is not the CD device."

I'm still wondering if there is something wrong with the CD and DVD. Both used to work by showing an icon on the desktop when you put in a CD or DVD. In the terminal I've typed 'mount cdrom' and got the reply 'can't find cdrom in /etc/fstab or /etc/mtab.
I'm the only user of this machine; though I do have 2 accounts. Thanks for your time and help...............Sarum

---

