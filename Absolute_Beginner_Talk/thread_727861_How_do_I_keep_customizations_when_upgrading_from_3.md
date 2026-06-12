---
title: "How do I keep customizations when upgrading from 32 to 64 bit?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-18
So when I first installed ubuntu I was naive and young.  I didn't realize that my CPU was 64 bit and didn't understand the reasons why I  would want 64 bit Gutsy.  I also didn't create a /home partition (I'm still not sure why you would want to... feel free to explain) but I really would like to upgrade from 32bit Gutsy to 64bit Gutsy.

The only thing I'm worrying about is I have a lot of customizations. I have a lot custom files like: .bashrc .dircolors .nanorc xmodmappings etc...  In fact  i have customized so many things I don't think I can list them out.

I want to upgrade to 64 bit gutsy but I really don't want to spend HOURS figuring out how to restore all the customizations I did by hand.

Is there anyway that I can package up all my customizations for use after I install the 64 bit system?

---

### Post by hyper_ch on 2008-03-18
user based customizations are stored in your home folder... so backup the /home folder....

server wide configuration is stored in the /etc folder... depending on what you installed/done you might also want to backup that one.

The config files do not depend on whether the architecture is 32- or 64-bit... so basically backup your /home folder, install the 64-bit version, install all software, put your home folder back.

---

### Post by scragar on 2008-03-18
2 solutions:
1 - backup your entire /home directory, install 64 bit ed, restore /home

2 - if you install it along side your previous install Gusty will let you copy your config files over, you can then use the liveCD to remove the old version and add the space to your new install.

---

### Post by neurostu on 2008-03-18
Will i face any permissions or ownership issues when I copy the folder over

---

### Post by hyper_ch on 2008-03-18
use the cp -P to copy with the according permissions.... first user will have user ID 1000... if you have created more users you might need to alter them afterwards.

---

### Post by scragar on 2008-03-18
you could always just chown them to the right user:```
sudo chown -R $USER ~/
```

---

### Post by hyper_ch on 2008-03-18
well, the uid 1000 is the "sudo" user so that one should stay intact when restoring ;)

---

