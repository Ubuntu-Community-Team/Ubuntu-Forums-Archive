---
title: "No USB in Virtual box? (It is enabled)"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-10-09
Gives me an error like this when ever I plug in the printer I added in the usb area. Also there are no usb options in the printer adding section in windows, USB is enabled. What to do?

(I cant post the error just yet, my mom is sing the VM Windows right now)

---

### Post by ~~Tito~~ on 2007-10-09
Anyone? The printer is a Brother HL-5240. I don't have the install cd sadly. . .

---

### Post by bodhi.zazen on 2007-10-09
[http://ubuntuforums.org/showpost.php?p=2366065&postcount=72](http://ubuntuforums.org/showpost.php?p=2366065&postcount=72)

---

### Post by ~~Tito~~ on 2007-10-09
THANKS!!

Will give it a try.

Trying Active sync now.

---

### Post by ~~Tito~~ on 2007-10-09
Nope. ..  I enabled the thing in the file, and enabled the device in the Virtual Box settings and I connect and it gives me this error.

[IMG]http://i72.photobucket.com/albums/i189/tito0096/Screenshot-4.png[/IMG]

---

### Post by bodhi.zazen on 2007-10-09
oci, is windows you host OS or guest ?

---

### Post by ~~Tito~~ on 2007-10-09
I don't know, I just host it? I run it in Virtual Box, thats all I know. Where do I go to find this out? Ubuntu is my main os.

---

### Post by bodhi.zazen on 2007-10-09
Sorry, host = main os

So you are running Windows on VirtualBox = Windows = guest OS

Try rebooting to see if those changes then take effect.

---

### Post by ~~Tito~~ on 2007-10-09
Ok, lol. Now I know. The whole system? Also there is this problem that the premissons for the vbox something in some folder keeps going back to rot and I havbe to change the permissions every reboot or VB wont work. . . IS there a way to permanently make it so I have permisons?

---

### Post by mmarshall on 2007-10-09
Sounds like you need to add your user the the vboxusers group.

---

### Post by ~~Tito~~ on 2007-10-09
Yea. Look at attachments. Ok, I checked I am on it. But why does it show this everytime. . .

---

### Post by bodhi.zazen on 2007-10-09
As mmarshall indicated, you need to add your user to the vboxusers group. Once you have done that, you then need to log out and back in for the changes to take effect. Good time to re-boot the host ... (Ubuntu)

---

### Post by ~~Tito~~ on 2007-10-09
Oh, Man. . . I wish I had outlook only. I cant sync my contacts. . .

---

### Post by ~~Tito~~ on 2007-10-09
> **bodhi.zazen said:**
> As mmarshall indicated, you need to add your user to the vboxusers group. Once you have done that, you then need to log out and back in for the changes to take effect. Good time to re-boot the host ... (Ubuntu)

What about if I added my self to the root group?

---

### Post by bodhi.zazen on 2007-10-09
> **~~Tito~~ said:**
> What about if I added my self to the root group?

why ?

---

### Post by ryanVickers on 2007-10-09
I never got USB working in VirtualBox, but I've never needed it!  I can share a folder between them just fine, and anything to do with devices (other than the odd CD) I do in Linux! ;)

---

### Post by ~~Tito~~ on 2007-10-10
Yea, but what about active sync and printers not working (not well but working) in Linux?
It should be resolved by now. Thanks guys. I am gonna leave this open incase I have other problems with USB devices.

---

### Post by ~~Tito~~ on 2007-10-15
Why wont my printer work? It shows the same error as what my blackjack did? My blackjack shows that error occasionally but it connects when it does. Whats the delio? It also shows when I enable the port for the parallel port?

---

### Post by ~~Tito~~ on 2007-10-15
Anyone?

---

### Post by ~~Tito~~ on 2007-10-16
Anyone, please? I need this fixed!

---

### Post by jellyman on 2007-10-18
I had problems with HP PSC 1210 USB printer in VIRTUAL BOX and also VMWARE PLAYER  when running winxp in ubunty feisty as host.

The printer only worked some times and the scanner would never work as it was never detected.  I tried everything but could never get the pprinter or scanner to work properly.

I solved the problem accidentally when I had BOTH VMWARE PLAYER and VIRTUAL BOX installed at the same time with winxp as guest.

Now the printer and scanner works perfectly when I am running virtual box or vmware player - and I didn"t have to mess about with any files etc.  

This solution works for me!!

---

