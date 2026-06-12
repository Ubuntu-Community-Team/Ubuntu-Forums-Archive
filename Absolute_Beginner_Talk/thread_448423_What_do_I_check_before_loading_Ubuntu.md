---
title: "What do I check before loading Ubuntu?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Deros on 2007-05-19
Hi, I'm trying out Ubuntu and have the liveCD running thanks to all the great links and information you guys provided.  The common advice seems to be to run the liveCD and check for hardware issues but I don't really know what to check for.

I'm using a HP with CD-ROM and CD-RW drives, 1.1Ghz Celeron processor and not sure about video or sound cards.  The computer does not have any important information, it was given to me by a friend and is a spare.  

So what tests or checks should I do before installing Ubuntu?
Thanks,
Deros

---

### Post by hyper_ch on 2007-05-19
Well, the most troublesome stuff is the videocard and wifi-card (if you have any)... the rest should be auto-recognized... download the live-cd, burn it, test it :) if the live-cd doesn't work... well, then is the option of using the alternate or you could start checking why the live-cd doesn't work.

---

### Post by overdrank on 2007-05-19
> **Deros said:**
> Hi, I'm trying out Ubuntu and have the liveCD running thanks to all the great links and information you guys provided.  The common advice seems to be to run the liveCD and check for hardware issues but I don't really know what to check for.

I'm using a HP with CD-ROM and CD-RW drives, 1.1Ghz Celeron processor and not sure about video or sound cards.  The computer does not have any important information, it was given to me by a friend and is a spare.  

So what tests or checks should I do before installing Ubuntu?
Thanks,
Deros

Hi you can run lspci command in the terminal ( located under applications, accessories) and find you video, sound and lan card then you can search here in the forums and see if they work well in ubuntu. Hope that helps. Good luck and welcome!:)

---

### Post by mikewhatever on 2007-05-19
Running the live CD is a test. Do you get a working desktop? Do you get right screen resolution? Is there sound? Is there internet connection?

---

### Post by Deros on 2007-05-19
Guys, thanks for the quick responses, this forum moves fast!  I do have a working desktop, sound ect.  Everything seems to work well.  No wireless so that is not a problem and I have not tried the internet yet.  
The LAN card is what I am most interested in as I want to use this for an internet server.


I tried Ispci in the terminal and it did not see to work.  

When I click on Terminal I get:
ubuntu@ubuntu:~$  

with a flashing cursor after it.

I type:
Ispci

and get:
bash:  Ispci:  command not found
ubuntu@ubuntu:~$  

What am I doing wrong?

---

### Post by soonindallas on 2007-05-19
did you type:
```
lspci
```
?

---

### Post by Deros on 2007-05-20
Yup, I did try 

1spci

and got the same message about command not found

What am I supposed to be typing here?

Thanks,
Deros

---

### Post by southernman on 2007-05-20
that's* l(letter)spci*... not *1(one)spci*

---

### Post by 56seeker on 2007-05-20
that's LSPCI; not 1SPCI  (it can be hard to see the difference between a lower case "L" and a "1" sometimes)

The command has to be in lower case.

---

### Post by hyper_ch on 2007-05-22
```

lspci

```
Means as much as *list pci devices*

There's also a
```

lsusb

```

Have a guess what lsusb does ;)

That way it's simple to remember :)

---

### Post by mikewhatever on 2007-05-22
Try this then
> sudo lshw -C network

---

