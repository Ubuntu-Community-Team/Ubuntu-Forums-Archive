---
title: "Asus Lan Drivers"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-05
I plan on finishing my new build next week and am using an A8N-SLI
Asus motherboard.  There are many linux options for lan drivers  2.2.25,2.4.13,2.4.22, and 6.16.
I am not very good at installing .tar files yet(I have made a few attempts)I succeed half the time with good instructions.

I guess since my LAN,Audio,and USB are all integrated.  Will I need to install all of these drivers from my mobo CD as .tar files or will the install automatically detect this and work out of the box without installing all of these?

Thanks

---

### Post by apjone on 2006-11-05
built an asus yesturday and i am usingit now, it worked fine with the fresh install, no drivers needed (apart from my nvidia gforce card lol)

---

### Post by gentlemanmasher on 2006-11-05
Great news I really appreciate your help this will save me some worrying for the next week.  Did you use the nvidia drivers found on automatix for the gforce card.  They worked very well for the 6600GT I am using right now.

---

### Post by apjone on 2006-11-05
i used the following, for my new card and the card in the last machine i used
works great
[http://ubuntuforums.org/showthread.php?t=239049](http://ubuntuforums.org/showthread.php?t=239049)

---

### Post by gentlemanmasher on 2006-11-05
thanks again will use this for my build.:p

---

### Post by autocrosser on 2006-11-05
I've been using a Asua P5P800-SE board for quite a while--everything works--LAN is very good w/edgy's stock stuff--using the repository Nvidia drivers (well-I got a update from ubuntu-developers-list  Security update--I'll clue you in if you want)--with no problems--running a 6200V+

---

### Post by gentlemanmasher on 2006-11-05
please clue me in on anything. I like to look at as many options as possible.  My graphics card works well now but I would like to see all the alternatives.

---

### Post by autocrosser on 2006-11-05
First--are you going to use Edgy or Dapper?-- I have the testing (soon to be in incoming) repository for 8776 which "cures" some exploit issues with buffer-over-run. If you are going with Edgy, I'll just post the apt sources--if you're staying with Dapper, I'll have to find the post on Launchpad again....

---

### Post by gentlemanmasher on 2006-11-05
upgraded to edgy last week.  I have the driver from automatix 2 installed.  Do i need to uninstall that.  Also please do a detailed walkthrough as I am very new.  I am becoming more comfortable with the terminal and love using it.

Thanks

---

### Post by autocrosser on 2006-11-05
COOL!! so--in your /etc/apt/sources.list, add the following line--

deb [http://people.ubuntu.com/~kees/test-lrm-2.6.17.6-1/]("http://people.ubuntu.com/%7Ekees/test-lrm-2.6.17.6-1/") ./

and do a sudo apt-get update--sudo apt-get upgrade

You'll get the new 8776 drivers--if you have ANY problems (no matter how weird or small) goto LaunchPad & search for the Nvidia thread & report--you'll get the best 8xxx series drivers & help the community to boot!

---

### Post by autocrosser on 2006-11-05
Sorry--didn't see the add to your post---first, did you tell automatix to restore your sources.list to the pre-automatix setting after installing everything?  If not, I would need to see copies of a couple of files in your /etc/apt file:-k

to modify you sources.list--8)

sudo gedit /etc/apt/sources.list  in a terminal

paste the line in my prior post to the bottom

save the file

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install nvidia-settings

after installing "nvidia-settings" just type nvidia-settings in the terminal & take a look

If you want to have the settings control panel in a GUI way--right-click on a panel--add to panel--Custom Application Launcher & put nvidia-settings in the command box--customize as you want--or you can add it to your menu--right-click on the system menu & have fun!!

---

### Post by gentlemanmasher on 2006-11-05
I assume I didn't modify my sources after automatix because I am not sure how you would do it.  So can I just uninstall the nvidia drivers put in by automatix and try your suggestion?

---

### Post by autocrosser on 2006-11-05
You should just be able to modify your sources.list & do the apt-get update/upgrade--apt will tell you what packages it's upgrading--shoot me a copy of your /etc/apt/sorces.list (have to copy/paste it to your desktop & rename it by adding .txt to the end or the forum won't upload it) so I can look at it...

---

