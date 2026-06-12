---
title: "Configuring newly installed Ubuntu ."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by nooblet on 2007-06-19
Hey guys I installed ubuntu but the thing is I am getting no sound because there are no Linux drivers for X-Fi Xtreme Music sound card so please could some one tell me how to install my Intel 946GZIS driver and then use its onbaord sound card for sound :) ? And please also can you tell how to change the resolution of the desktop ? 
And how to install MSN Messenger on Ubuntu ?

---

### Post by nooblet on 2007-06-19
Please could somebody help me .

---

### Post by neotasic1 on 2007-06-19
> **nooblet said:**
> Hey guys I installed ubuntu but the thing is I am getting no sound because there are no Linux drivers for X-Fi Xtreme Music sound card so please could some one tell me how to install my Intel 946GZIS driver and then use its onbaord sound card for sound :) ? And please also can you tell how to change the resolution of the desktop ? 
And how to install MSN Messenger on Ubuntu ?

I am no expert at this but normally you don't need to install sound drivers.  In your system bios, you will have to disable your sound card (this may mean you may have to physically remove it from it's PCI slot) and enable the onboard sound chip - this varies from pc to pc so I can't give you specific instructions, but if you post which bios you have someone will probably help.  It then depends as to whether Linux has drivers for you onboard sound - I don't know this but it can't hurt to try it out.  

You can change screen resolutions by clicking on System>Preferences>Screen resolution and selecting the resolution you want. If it is not available, then it depends on which video card you have as to how to go about it.  

You may need to post details of your video card onto the forum and wait patiently for an answer.  (this can take hours and occasionally days if it is something others haven't come across yet.  If you Google search while you wait for help you may find the answer yourself and save time - you never know:)

As to MSN I don't use it, but there are Linux variants Applications>Internet>Gaim Internet Messenger is a good place to start.

---

### Post by nooblet on 2007-06-19
So the thing about the Sound Card my sisters use Windows XP so if I disable the sound card from BIOS it will be disabled for XP too :( ....... is there any other way ?

---

### Post by neotasic1 on 2007-06-19
> **nooblet said:**
> So the thing about the Sound Card my sisters use Windows XP so if I disable the sound card from BIOS it will be disabled for XP too :( ....... is there any other way ?

Try System>Preferences>Sound and check to see if you have options as to which sound device to use, you may find that Linux knows about your onboard chip and will allow you to use it.  Other than that, I don't know as I am new to this also.

---

### Post by 00arthuryu on 2007-06-19
just for a note, if you're looking for something like msn on linux, you might want to try amsn
```

sudo apt-get install amsn

```

---

### Post by nooblet on 2007-06-19
Well I don't know how to use the Terminal at all :P I am new to linux to I don't know any commands ...

---

### Post by Crafty Kisses on 2007-06-19
> **00arthuryu said:**
> just for a note, if you're looking for something like msn on linux, you might want to try amsn
```

sudo apt-get install amsn

```

That client always crashes. :(

---

### Post by nooblet on 2007-06-19
IT didnt crash for me :p

---

### Post by Jimmyfj on 2007-06-19
For the on-board sound card you should check whether is deactivated  in the BIOS. Obviously if it is there's no driver installed for the device.

As for aMSN: Go to Programs/add-remove/internet and mark up the aMSN from there.

To adjust resolution I normally use Sysinfo for the settings for my nVidia graphics card. With the restricted driver installed I have access to the settings the above way.

---

### Post by Crafty Kisses on 2007-06-19
> **nooblet said:**
> IT didnt crash for me :p

Great for you. :KS

---

### Post by nooblet on 2007-06-19
Ehh when I installed the nvidia drivers for my 8800GTS through the Restricted Drivers thingy and restarted pc Ubuntu crashed and it showed some X server error on a gray page ..... so I had to reinstall Ubuntu twice cos I installed nvidia drivers twice :( third time I have not installed them till now ...

---

### Post by laura_glow on 2007-06-19
you could try gaim too, it also has icq, yahoo and gtalk (jabber)
run adept package manager and search for gaim. ("start"->system->Adept Manager)

---

