---
title: "how does synaptic work?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Drone4four on 2007-07-09
I'm trying to install libdecoration0 with synaptic.  I've searched, found and marked the library.  Now  how do I install them?  There is no install button.  wtf?

---

### Post by jordanmthomas on 2007-07-09
Use the Apply Button.
You may want to read this:
[http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic)

---

### Post by xxchrisxx555 on 2007-07-09
at the top there is a button that says apply

---

### Post by qamelian on 2007-07-09
> **Drone4four said:**
> I'm trying to install libdecoration0 with synaptic.  I've searched, found and marked the library.  Now  how do I install them?  There is no install button.  wtf?

Click on the Apply button to apply the changes you selected (eg ,libdecoration0 marked to install).

---

### Post by rocknrolf77 on 2007-07-09
Yes, it's the apply button :)

---

### Post by Drone4four on 2007-07-09
hmm, my apply button is greyed out...it's not clickable...wtf?

---

### Post by jordanmthomas on 2007-07-09
Are you absolutely sure you marked the package for install?

---

### Post by Drone4four on 2007-07-09
> **jordanmthomas said:**
> Are you absolutely sure you marked the package for install? yes i am absolutely sure the two little boxes have tick marks in them.  hmm, when i click properties, there is a dependency conflict with compiz-core

---

### Post by ramjet_1953 on 2007-07-09
After you have selected the package that you want to install, just click on the "Apply" button in the top toolbar of Synaptic.

Regards,
Roger 8)

---

### Post by Drone4four on 2007-07-09
i feel like such a newb

---

### Post by deadlikeoscar on 2007-07-09
Are you trying to install Compiz Fusion?

---

### Post by jordanmthomas on 2007-07-09
Well if all else fails, you could always just use apt-get.
```
sudo apt-get install libdecoration0
```

It'll tell you if there's any reason you can't install it.

---

### Post by rocknrolf77 on 2007-07-09
Have a look at [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu) and [www.ubuntuguide.org](www.ubuntuguide.org) and I'm shure you will learn a lot more. You just need where to look for answers :)

---

### Post by Drone4four on 2007-07-09
> **jordanmthomas said:**
> Well if all else fails, you could always just use apt-get.
```
sudo apt-get install libdecoration0
```

It'll tell you if there's any reason you can't install it.

hmm, even after installing libdecoration with your command, compiz fusion still doesn't work.  Here is my thread: [http://ubuntuforums.org/showthread.php?p=2994144#post2994144](http://ubuntuforums.org/showthread.php?p=2994144#post2994144)

---

### Post by Drone4four on 2007-07-09
> **deadlikeoscar said:**
> Are you trying to install Compiz Fusion?yes

---

### Post by Drone4four on 2007-07-09
> **rocknrolf77 said:**
> Have a look at [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu) and [www.ubuntuguide.org](www.ubuntuguide.org) and I'm shure you will learn a lot more. You just need where to look for answers :)

thanks

---

### Post by stepan2 on 2007-07-09
are you sure you are running in root??if you started synaptic from the command line without sudo it wont run as root.

---

### Post by deadlikeoscar on 2007-07-09
I think you need to uninstall everything compiz related under Synaptic (which will prompt to remove ubuntu-desktop) and then install compiz fusion. (And ubuntu-desktop if it doesn't reinstall automatically) I had trouble with mine because I didn't know you had to uninstall compiz but I eventually got it to install in Synaptic by messing around but I don't remember what I did.

---

### Post by stepan2 on 2007-07-09
i dont understand. How is removing a program going to fix anything . And isn't the program not installed?Also , if you remove ubuntu-desktop then  you will  be left for the command line. I think he is new to linux and that will force him to move back to the dreaded OS

---

### Post by jordanmthomas on 2007-07-09
> if you remove ubuntu-desktop then you will be left for the command line.
a little off-topic, but ubuntu-desktop is just a meta-package and if you remove it the only thing that will happen is you might not get a piece of software the devs think should be included by default (ie updating to the next Ubuntu will not go as expected)

---

### Post by deadlikeoscar on 2007-07-09
> **stepan2 said:**
> i dont understand. How is removing a program going to fix anything . And isn't the program not installed?Also , if you remove ubuntu-desktop then  you will  be left for the command line. I think he is new to linux and that will force him to move back to the dreaded OS

Because the OP said that libdecoration0 is conflicting with compiz and Synaptic won't install it. I'm pretty sure if you look at the Compiz Fusion sticky on these boards it says the same thing.

Edit: Here is the sticky: [http://ubuntuforums.org/showthread.php?t=481314]("http://ubuntuforums.org/showthread.php?t=481314")

---

### Post by ramjet_1953 on 2007-07-10
Don't feel like that!

This is something so different that quite often things aren't obvious.

Just stick with it and I guarantee that you will be very comfortable within a few months.

Don't forget, it has taken you years to learn Windows, so don't expect to be able to use Linux overnight.

Another thing that can be confusing, is that Linux often has several ways to do the same thing. Again, after some time, you will learn the subtle differences between them.

Regards,
Roger :cool:

---

