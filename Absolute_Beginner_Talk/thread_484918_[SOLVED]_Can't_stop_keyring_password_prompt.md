---
title: "[SOLVED] Can't stop keyring password prompt"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-06-17
what is keyring for? actually it appeared when i was attempting to save the wireless network password,  and if it is a super password for other passwords does it require to enter the super password every login??? cuz after i saved keyring password (to let me able saving the wireless network password) it requires to enter the keyring password every time i log in to the system ,
so any ideaaaa?

---

### Post by icechen1 on 2007-06-17
there is an annoying problem with  the keyring that ask you the password each login.A fix is at [http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring) (you don't have to compile the pam_keyring,it is in the repos.)

---

### Post by andrei.kouznetsov on 2007-06-17
The question was "what is keyring for?". I have the same question, because "Keyring manager" shows all passwords in the keyring, but when you start "Keyring manager", it does not ask for a password.
Does it mean that you can store only public keys in the keyring?

---

### Post by akkad on 2007-06-20
ok i did sudo gedit /etc/pam.d/gdm
and then added 
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

but it still request keyring login every boot, i have two keyrings that appear in the keyring manager, one with name default and the other is session, any other solution ????

---

### Post by Inxsible on 2007-06-20
A keyring is a file where all your network passwords are stored and is itself encrypted with a password.
 
If you connect to multiple wireless connections, then instead of remembering all passwords, you can simply remember the keyring password and be done with it. 
A keyring password should be different than your login password or your network password for the very fact that no one else can access any of your networks even from your own computer, if you havent supplied your keyring password to them. 
 
Of course, this leads to an annoying password box every time nm-applet tries to get online. There are ways to get around this as listed before of course.

---

### Post by whiteguysamurai on 2007-06-20
I agree, the keyring is VERY annoying.
And sometimes it doesn't work with a usb keyring like it should.

---

### Post by holscher on 2007-06-24
a simple solution 
[http://ubuntuforums.org/showthread.php?t=479926](http://ubuntuforums.org/showthread.php?t=479926)

---

### Post by akkad on 2007-06-26
on login screen it asks me to enter password two times, this is a new behavior which wasnt there before where previously i used to enter it one time, how to get back again to the old behavior?

---

### Post by w4ett on 2007-06-26
Sounds like a video driver issue.....Are you using a restricted driver?   Here's a fix for Nvidia:

[http://ubuntuforums.org/showthread.php?t=452596&highlight=login+twice](http://ubuntuforums.org/showthread.php?t=452596&highlight=login+twice)

Bottom line is to uninstall your restricted driver  and then reinstall, restart X, and it should be fixed.

---

### Post by akkad on 2007-06-26
actually not, my vga is ATI , this behavior appeared after i edited some settings for the keyring.

---

### Post by w4ett on 2007-06-26
Are you using the restricted drivers or the open source drivers?  Might be worth a try to remove them and then reinstall the driver and see if it works.....

---

### Post by akkad on 2007-06-26
i do use them, but am really afraid to do anything with the display drivers cuz am using 3d desktop and it was really hard  to accomplish this , so do u assure me that if i will reinstall the drivers nothing will be damaged?? if so then how to do the reinstall process, i dont know how to do it :( .

---

### Post by akkad on 2007-07-18
i have edited some configuration for keyring to stop asking for the keyring password in every login where it went fine, but after that the login screen started to ask me to enter the password twice to be able to login, any idea how to make it ask for the password just one time ???

---

### Post by aysiu on 2007-07-18
I've merged your multiple threads on the same topic. Please keep it down to one thread per support topic. Thanks.

---

### Post by akkad on 2007-07-18
sorry but i was looking for an answer i was seeking since along time.

---

### Post by akkad on 2007-07-18
on the forum they suggested me to edit the file : /etc/pam.d/gdm by adding the following :
auth	optional	pam_keyring.so try_first_pass
session	optional	pam_keyring.so

---

### Post by aysiu on 2007-07-18
Well, you got the answer, but the libpam-keyring solution will work only if your keyring manager password and login password are the same. Are they?

---

### Post by akkad on 2007-07-18
nooo aysiu  keyring is not my problem any more it is fixed, but after i fixed it the login screen requires me to enter the login password two times to be able to login not only one time.
anyway yes keyring password and login password are the same

---

### Post by aysiu on 2007-07-18
Great, akkad. Thanks for sorting out the confusion. I've separated out two threads and retitled them appropriately. One (this one) is on the keyring issue and marked as solved. The other one about being asked for the password twice at login is [its own thread.](http://ubuntuforums.org/showthread.php?t=503976)

---

### Post by akkad on 2007-07-18
thnx and sorry for this confusion.

---

