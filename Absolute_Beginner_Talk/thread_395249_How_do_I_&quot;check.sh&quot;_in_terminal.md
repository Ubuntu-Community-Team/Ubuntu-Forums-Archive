---
title: "How do I &quot;check.sh&quot; in terminal?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-27
I need to run check.sh in terminal. I have the file check.sh on my desktop. What do I enter in terminal to locate and run check.sh?
Thanks for the help.
kh

---

### Post by tonyr1988 on 2007-03-27
First, go to your Desktop:

> cd ~\Desktop

cd = Change Directory
~\Desktop = Your Desktop! :)

Then, run the script with:

> sh check.sh

*Cool tip: * In the Terminal, there is a thing called Tab-Completion. When typing that last command, do this:

> sh che

and then hit the Tab key. Viola! Pretty cool, huh? (if you have other files in your Desktop starting with che____, you'll have to hit Tab twice)

---

### Post by martinw89 on 2007-03-27
Try these commands:
```
cd ~/Desktop
chmod +x check.sh
./check.sh
```
Quick rundown: "cd ~/Desktop" **c**hanges the **d**irectory to the Desktop folder, inside your home folder
"chmod +x check.sh" **ch**anges the **mod**e so that the file can be e**x**ecuted
./check.sh runs the file

Hope that helped!

---

### Post by kittyhawk63 on 2007-03-27
> **tonyr1988 said:**
> First, go to your Desktop:
cd = Change Directory
~\Desktop = Your Desktop! :)
Then, run the script with:
*Cool tip: * In the Terminal, there is a thing called Tab-Completion. When typing that last command, do this:
and then hit the Tab key. Viola! Pretty cool, huh? (if you have other files in your Desktop starting with che____, you'll have to hit Tab twice)

Thanks, I did this earlier but it didn't work. I'll try it again.
kh

---

### Post by kittyhawk63 on 2007-03-27
> **martinw89 said:**
> Try these commands:
```
cd ~/Desktop
chmod +x check.sh
./check.sh
```Quick rundown: "cd ~/Desktop" **c**hanges the **d**irectory to the Desktop folder, inside your home folder
"chmod +x check.sh" **ch**anges the **mod**e so that the file can be e**x**ecuted
./check.sh runs the file
Hope that helped!

Did not work.
I ran each line separately and then all together.
kh

---

### Post by martinw89 on 2007-03-27
Are you sure it's a proper script?  Are you sure it isn't owned by root?  If it's owned by root, just add sudo before the last two commands.

---

### Post by kittyhawk63 on 2007-03-27
> **martinw89 said:**
> Are you sure it's a proper script?  Are you sure it isn't owned by root?  If it's owned by root, just add sudo before the last two commands.

It's directly downloaded from the web page. I will add sudo and see what happens.
kh

---

### Post by tonyr1988 on 2007-03-27
Are you getting any errors?

If it complains about permissions, try:

> cd ~\Desktop
sudo chmod 777 check.sh
./check.sh

(it's not the most optimal solution, but it's a catch-all)

---

### Post by kittyhawk63 on 2007-03-27
Here is what I typed and the replies:

kittyhawk63@kittyhawk63:~$ cd ~/Desktop
kittyhawk63@kittyhawk63:~/Desktop$ sudo chmod +x check.sh
Password:
kittyhawk63@kittyhawk63:~/Desktop$ sudo ./check.sh
===================================================================== ATI Technologies
=====================================================================You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

kittyhawk63@kittyhawk63:~/Desktop$

---

### Post by kittyhawk63 on 2007-03-27
> **tonyr1988 said:**
> Are you getting any errors?
If it complains about permissions, try:
(it's not the most optimal solution, but it's a catch-all)

Same results as before.
kh

---

### Post by slayerboy on 2007-03-27
> **kittyhawk63 said:**
> Here is what I typed and the replies:

Unable to determine XFree86 Version. Stopping now.


Methinks this could be because Ubuntu uses XOrg, not XFree86 :confused:


What are you trying to install from ATI?

---

### Post by tonyr1988 on 2007-03-27
Try this (read this whole post before you start, or you'll be lost):

Ctrl+Alt+F1 will drop you to a console (pure black and while...will remind you of DOS). Login with your username and password. Try the same commands:

> cd ~\Desktop
sudo ./check.sh

See if that works. Either way, to get back to your graphical Ubuntu, do:

Ctrl+Alt+F7

EDIT: slayerboy is probably right...I didn't get to the XFree86 part.

---

### Post by kittyhawk63 on 2007-03-27
I dbl-clicked the file and it asked if I wanted to run it in terminal. I said yes. Terminal opened, something happened and terminal closed too fast for me to see what happened.

---

### Post by kittyhawk63 on 2007-03-27
> **tonyr1988 said:**
> Try this (read this whole post before you start, or you'll be lost):
Ctrl+Alt+F1 will drop you to a console (pure black and while...will remind you of DOS). Login with your username and password. Try the same commands:
See if that works. Either way, to get back to your graphical Ubuntu, do:
Ctrl+Alt+F7
EDIT: slayerboy is probably right...I didn't get to the XFree86 part.

Same results.
kh

---

### Post by kittyhawk63 on 2007-03-27
Here is where I downloaded the file. Would you mind seeing if I did the wrong thing? I went to the section for Dapper. check.sh is shown there.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by kittyhawk63 on 2007-03-27
> **slayerboy said:**
> Methinks this could be because Ubuntu uses XOrg, not XFree86 :confused:
What are you trying to install from ATI?
Sorry, I missed your post.
I am trying to download a driver for ATI Radeon 9200SE. The default driver freezes the screen eventually. 
Maybe I can't use the driver that I found. It is listed as 8.28.8 driver for my card. Earlier when I used one it froze me out of Ubuntu altogether.
kh

---

### Post by kittyhawk63 on 2007-03-28
I'm stopping this thread. I don't think I will be able to solve it. I've been working at it for over a month.
kh

---

### Post by slayerboy on 2007-03-28
WAIT.....I don't see a reference to check.sh in that link you posted....where did you get that?

Did you install following the ububtu way or the manual way?

---

### Post by slayerboy on 2007-03-28
type this:

fglrxinfo

and copy and paste the info it spits out....please :)

---

### Post by kittyhawk63 on 2007-03-28
> **slayerboy said:**
> WAIT.....I don't see a reference to check.sh in that link you posted....where did you get that?
Did you install following the ububtu way or the manual way?

You're right. Got too much in a hurry and gave the wrong page. I will find it and list it in a minute or two. Thanks for the correction.
kh

---

### Post by alienexplorers on 2007-03-28
What exactly is check.sh suppose to do.  I checked your link to and could find no reference to check.sh......

---

### Post by martinw89 on 2007-03-28
I'm pretty sure that in Dapper, the newest ATI release is 8.25.18 ([here]("http://packages.ubuntu.com/dapper/misc/xorg-driver-fglrx")).  So running```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
``` and then ```
sudo depmod -a
sudo aticonfig --overlay-type=Xv
``` should work for you, because it will install older drivers that will work with your legacy card.

Edit: Don't forget to reboot after installing the drivers

---

### Post by kittyhawk63 on 2007-03-28
I can't find the page. Don't know what I typed in Google.  Sorry.
kh

---

### Post by kittyhawk63 on 2007-03-28
> **slayerboy said:**
> type this:
fglrxinfo
and copy and paste the info it spits out....please :)

I tried it with and without sudo:

kittyhawk63@kittyhawk63:~$ sudo fglrxinfo
Password:
sudo: fglrxinfo: command not found
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-03-28
> **martinw89 said:**
> I'm pretty sure that in Dapper, the newest ATI release is 8.25.18 ([here]("http://packages.ubuntu.com/dapper/misc/xorg-driver-fglrx")).  So running```
sudo apt-get install xorg-driver-fglrx
``` and then ```
sudo aticonfig --overlay-type=Xv
``` should work for you, because it will install older drivers that will work with your legacy card.

I've used this numerous times and that is when I start having screen freezes or get locked out of Linux completly on boot up.
So far without updates I have had no screen freezing. I've been online for over an hour. It always freezes within ten to fifteen minutes.  That is why I would like to know if there is an update that causes this problem.
kh

---

### Post by martinw89 on 2007-03-28
Sorry I couldn't help anymore, good luck on finding a solution :)

-Martin

---

### Post by kittyhawk63 on 2007-03-28
> **martinw89 said:**
> Sorry I couldn't help anymore, good luck on finding a solution :)
-Martin

Thank you for your help.
kh

---

### Post by tonyr1988 on 2007-03-29
I've got one more try at this (sorry it's taking you so long to get a relatively simple thing working).

Earlier, when I told you to Ctrl+Alt+F1 to use a "real" console, I didn't think about the fact that you still have X running in the F7 terminal. Try to completely kill X (Ctrl+Alt+Backspace - it will destroy any windows or programs you have running, so save and close everything). You will be kicked back to your login screen. Ignore it.

Go back to Ctrl+Alt+F1 and try the steps again (cd ~\Desktop, sh ./check.sh) and see if you get the same error. Either way, when you're done, Ctrl+Alt+F7 will bring you back to your login prompt.

---

### Post by martinw89 on 2007-03-29
> **tonyr1988 said:**
> I've got one more try at this (sorry it's taking you so long to get a relatively simple thing working).

Earlier, when I told you to Ctrl+Alt+F1 to use a "real" console, I didn't think about the fact that you still have X running in the F7 terminal. Try to completely kill X (Ctrl+Alt+Backspace - it will destroy any windows or programs you have running, so save and close everything). You will be kicked back to your login screen. Ignore it.

Go back to Ctrl+Alt+F1 and try the steps again (cd ~\Desktop, sh ./check.sh) and see if you get the same error. Either way, when you're done, Ctrl+Alt+F7 will bring you back to your login prompt.
When you get kicked back to your login screen it means that X has restarted, because of GDM.  To stop GDM just type "sudo /etc/init.d/gdm stop" in a CTRL+ALT+F1 terminal :)

---

### Post by tonyr1988 on 2007-03-29
> **martinw89 said:**
> When you get kicked back to your login screen it means that X has restarted, because of GDM.  To stop GDM just type "sudo /etc/init.d/gdm stop" in a CTRL+ALT+F1 terminal :)
Sorry about that - it was too late last night for me to be trying to think. :)

---

### Post by kittyhawk63 on 2007-03-29
I wish to thank each of you for your help. I reloaded Linux again last night. I reran all the sudo commands to install fglrx for my video driver. I left out one line purposely. That is the line: [COLOR=Blue]sudo aticonfig --overlay-type=XV  [/COLOR]I had missed this line earlier when I had my video working fine. Since I saw it, I had included it and that is when I started having video problems "again". I am trying to see if that may have been my problem this time. I am still looking for that page where I downloaded the "check.sh" file. I will post it when I find it.
Thanks again.
kh

---

### Post by kittyhawk63 on 2007-03-29
[http://ati.de/support/drivers/linux/linux-radeon-prer200.html](http://ati.de/support/drivers/linux/linux-radeon-prer200.html)

This is the page for the check.sh file that I downloaded.

I see now that it is not what I needed. I am using xorg, not XFree86. That is why I was getting errors that it could not find the file. Thanks for your help. It helped me to see where my mistake was.
kh

---

### Post by tonyr1988 on 2007-03-29
So is everything working alright now, or is there another part of the installation being a pain? Sorry you had so many problems with that evil shell script. :)

---

### Post by kittyhawk63 on 2007-03-29
> **tonyr1988 said:**
> So is everything working alright now, or is there another part of the installation being a pain? Sorry you had so many problems with that evil shell script. :)

Yes, everything seems to be working alright. I understand thatI can use a better driver than fglrx. I am checking into that. This fglrx is a real pain to get working. I found through experiment that the line sudo anticonfgi --overlay-type-Xv was probably causing my headaches. I left it out and so far (fingers crossed) I've not had a crash.
Thanks for your enquiry and your assistance.
kh

---

### Post by tonyr1988 on 2007-03-29
Sorry I couldn't help much, but I'm glad things are working.

If you get a chance, could you mark this thread as Resolved? Edit the first post, click Go Advanced, and you'll see the checkbox right under the title. It helps a lot for keeping the forums clean (it won't delete your thread, just mark it as Resolved)

---

### Post by kittyhawk63 on 2007-03-29
> **tonyr1988 said:**
> Sorry I couldn't help much, but I'm glad things are working.

If you get a chance, could you mark this thread as Resolved? Edit the first post, click Go Advanced, and you'll see the checkbox right under the title. It helps a lot for keeping the forums clean (it won't delete your thread, just mark it as Resolved)

Got it. Thanks for the reminder on resolved.
kh

---

### Post by slayerboy on 2007-03-30
glad it's all worked out :)

---

