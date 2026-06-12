---
title: "Couple of Ubuntu/Kubuntu questions"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-10-10
Hi, being new and doing cross over from Win98se I,m having a bit of a time finding out where U/K hide certain files/folders.
1. where do I put prgm pkgs so apt-get/synaptic can find?
2. is there a app that I can install that works like win Dial-up networkind ie: sits on/in tray bar & allows you to dial up & monitor your connection speed too? I have 4 numbers to connect with.
3. how can I get Kubuntu to recognize my modem, Ubuntu picked it up right away?
Thanks in advance for all replies.

PS: please keep in mind I'm the last "S" in KISS ](*,)

---

### Post by sumguy231 on 2006-10-10
1.) If it's a just some .debs, just use 'sudo dpkg -i <filename>' to install them. You will need to go fetch the dependencies yourself. (Edit: Which requires a net connection, I suppose you'll need to wait for #3.)
Sorry I can't answer 2 & 3 properly, it's been years since I've used dialup. I will, however refer you to the great and wise wiki:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by randiroo76073 on 2006-10-10
Thnx sumguy231, had read wiki previously, forgot to mention it's a external modem & suppose to be Linux friendly, but only Ubuntu picks it up.  Is there some settings I can transfer to Kubuntu that will help? :confused:

---

### Post by Paul133 on 2006-10-10
So your modem only works in Gnome? Then I'd recommend you use Gnome instead of KDE, at least until you have your machine set up.

---

### Post by randiroo76073 on 2006-10-10
Thanks Paul[LOL!] do I have much choice ;) I actually have 6 distros installed, Ubuntu, Kubuntu, Kanotix, Mephis, PCLinux, Freespire, but am concentrating on Ubuntu/Kubuntu so as to not get to confused, I don't just stick my toe in, oh no! I dive in head first & hope the water's not too cold. LOL!

---

### Post by randiroo76073 on 2006-10-11
Does anyone else have some answers for me as I would like to get Kubuntu internet ready too :)  1 distro at a time, I would like to get them all internet ready, course that might take me awhile LOL!

---

### Post by cmoman on 2006-10-13
KPPP might be the tool that you are looking for in Kubuntu.
The modem query button should pickup your external modem no problems.
/dev/modem should be symlinked to something like /dev/ttyS0 which translates to you COM1 etc.

ls /dev/modem > /dev/ttyS0

or else you can enter /dev/ttyS0 directly into KPPP and see if the query modem tool can pick it up.

---

### Post by randiroo76073 on 2006-10-13
cmoman, thanks for your reply.  I tried that[query modem] with no success, will try the entry way, so far, out of the 6 distros I have, Ubuntu is the only 1 that picked it up bang-zip.  The others I can't get to, even going thru the "dev" list...???  This month I'm getting a new monster drive[320gb] and am going to install all my linux on it w/separate Homes so if I reinstall I don't loose my settings.  Am I wacked or what? LOL!

---

### Post by cmoman on 2007-05-13
hello again.
i'm not sure if you are still following this post. i thought i would be reminded if you or anyone else posted to my previous message. i don't think i checked the correct box for email notification

the correct symlink command should have been

ln -s /dev/ttyS0 /dev/modem

ls -al /dev/modem would show if the symlink had been made correctly.

your suggestion of separate partitions is a fairly standard practice and gives you lots of flexibility. good luck on your linux adventure.

---

### Post by randiroo76073 on 2007-05-24
Thanks for checking back cmoman, got it all straight now :)  Since  1st post I've become a distro junkie, got 16 installed and lovin every minute!

---

