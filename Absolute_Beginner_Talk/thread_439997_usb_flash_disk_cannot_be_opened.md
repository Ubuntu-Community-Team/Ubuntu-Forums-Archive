---
title: "usb flash disk cannot be opened"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-11
it says "unable to mount the selected volume." when i clicked on "show more details",it said "error: this program need to be installed suid root" and "error: could not execute pmount".

how do i fix this so i can see the contents of my usb flash disk?

---

### Post by silkstone on 2007-05-11
Have you password protected the flash drive in Windows?

If so, you have to remove the password protection in Windows for the drive to be accessed in Ubuntu.

---

### Post by j_evenstar on 2007-05-11
no it doesn't have a password in windows. i have tried it yesterday and it worked fine, but today i cannot open its contents..
do i have to type any code?? thanks

---

### Post by j_evenstar on 2007-05-11
i really need help here..

---

### Post by esoterica on 2007-05-11
Windows password protection isn't going to prompt you for a super user root id. If you were under normal Linux it would be easy to su, I'm brand new to Ubuntu though and it's a little different with the sudo instead of root thing for me. WIndows Vista has done this same stuff, it took me forever to figure out how to do an "ipconfig /flushdns" from the command line in Vista because even logged in on an Administrator account it kept telling me I didn't have permission and wanted a password, the only password on the system didn't work, you have to actualy select to run the command line in Vista as Administrator first from the GUI.

I don't have an answer for you, but seeing as how your just hanging waiting for help anyhow I'd try to do just anything at all in Unbuntu that is going to prompmt you for the sudo password, I think I read somewhere it holds this active for 10 minutes once you log into it. Once it has you logged into the sudo priveledges it will problem allow you to perform what's requiring traditional root access now.

It's just a guess, but it's worth a try, I'm not even sure what to tell you to do to force the sudo log in, it's probably documented somewhere though, I know I was running apt-get earlier at the command line and was prompted for it. I think I also read somewhere about making a short cut to drives you want to mount with the sudo user as part of the link or something, it was somewhere listed as a user documentation tip or trick I found when reading the documentation on the main Ubuntu site.

---

### Post by esoterica on 2007-05-11
Found it, here's the link to what I was reading and thinking may help you in this situation...

[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

Once your logged in with the root account like this it should let you mnt the drive.

---

