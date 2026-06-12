---
title: "Thunderbird 2.0 won't start after a Netscape notification"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by atmartin50 on 2007-06-18
Hi All,

When I went to check my email this morning, I had a notification from Netscape pop up. As it was early and I was only half-awake, I quickly scanned through it and selected 'ok,' because I assumed it was an agent which reports crashes or bugs (I think I vaguely recall it saying "Would you like to participate?"). After I was unable to open Thunderbird, I shrugged it off as being just a temporary thing that a restart would fix. 

It turns out that this was incorrect, as I'm still unable to open Tbird. Does anyone have any ideas? I'd appreciate any help! Thanks in advance!

---

### Post by apjone on 2007-06-18
open a terminal and run thunderbird from the terminal, this will print out some garbage in the termainal . Read it and if you cant figure out whats up then copy it and post it here.

---

### Post by atmartin50 on 2007-06-18
Hi apjone,

Thanks for your quick reply. Here's what I got via the terminal:

atm@atm-laptop:~$ thunderbird
Segmentation fault (core dumped)

Any ideas?

Thanks a lot!

---

### Post by Seisen on 2007-06-18
You can try this link and see if it works. Let us know.

[http://ubuntuforums.org/showthread.php?t=423521]("http://ubuntuforums.org/showthread.php?t=423521")

---

### Post by atmartin50 on 2007-06-19
Thanks a lot Seisen! I really appreciate it!

Problem solved!:D

For any others having this problem, here's how to go about fixing it:

[Thunderbird, Firefox] Thunderbird doesn't start at all. Segmentation Fault (Core Dumped) when running from terminal

It could be due to a known incompatibility between Thunderbird/Firefox and SCIM. If you have SCIM installed and enabled, and you don't need it, you can try uninstalling the scim package with

sudo apt-get remove scim

and then try running Thunderbird again.

If you do need SCIM, a possible fix is to use one of the following commands to start Thunderbird:

export GTK_IM_MODULE=scim-bridge; thunderbird

or

export GTK_IM_MODULE=xim; thunderbird

If the above does work for you, you may want to change your Thunderbird shortcut to do it for you, so you don't have to start Thunderbird from a terminal all the time. To do that, follow these steps.

    * Create a text file with the following content, and save it in your home directory as "thunderbirdstarter.sh" 

#!/bin/bash
export GTK_IM_MODULE=scim-bridge; /usr/bin/thunderbird

    * Change the script to executable with command 

chmod u+x thunderbirdstarter.sh

    * Open the menu editor through Applications -> Accessories -> Alacarte Menu Editor
    * Find your Thunderbird shortcut, right click, select Properties
    * Change the shortcut to point to /home/your_username/thunderbirdstarter.sh 

Thunderbird should now start properly.

---

### Post by tomash_cz on 2007-06-22
thanks for help, i did exactly what you wrote and it worked perfectly. Just on one problem. I am using SCIM for writing chinese and after I made the changes the Thunderbird can be opened, but I can not use SCIM inside, it can write only english.

Do you have any idea or help how to solve it? Thanks.

---

### Post by atmartin50 on 2007-06-22
Wow, I just realized that I'm having the same problem! Thanks for pointing this out. However, I have no idea how to go about fixing it. I'll do some searching and let you know if I find out.

---

### Post by tomash_cz on 2007-06-23
atmartin50, thanks, as I remember I did not have this problem with Thunderbird 1.5, so I was almost about to uninstall 2.0 and keep the older version. But know this won't help solving the problem.

By the way, how do you work with skype and scim? Can you use SCIM input in skype? Just sharing another headache with you ;).

---

### Post by atmartin50 on 2007-06-23
I also never had this problem with v1.5. And I agree with you, going back to the old version would not necessarily fix the issue. Anyways, let's both do some research and let each other know if we find anything promising.;)

As to Skype, I read in a forum somewhere (perhaps it was here in Ubuntu Forums, but I'm not sure) that it is currently impossible to type Chinese in Skype for Linux. I should say it this way: you can type, sure, but 1 out of every 6-8 characters will come out as blocks or random symbols. This is definitely a headache.](*,) I've tried a few different versions for Linux in both Edgy and Feisty, and this is the case in all of them. Truly disappointing, as the chat feature was a quite way for my wife (she's Chinese) and I to trade messages back in my Windows days.

---

### Post by metapaso on 2007-06-28
I have this same problem with my system--just installed SCIM in order to write Japanese, and now my thunderbird won't start (segmentation fault).

I tried using the export command as per your instructions, but there's no trace of such a command on my system (Feisty 7.04)

Where do I find this export command?

Thanks,
Damon

---

### Post by atmartin50 on 2007-06-28
Hi Damon,

Though I'm now running Feisty, I was running Edgy at the time I used these instructions. I'm sorry to say that I have no idea about this 'export' command in Feisty.

Tomash_cz:

After upgrading from Edgy to Feisty, I downloaded the new Skype (version 1.4 beta), and discovered that Chinese can be typed (at least, it worked when I exchanged some chat messages with my wife, who runs Windows XP)! Good news:D

Aaron

---

### Post by tomash_cz on 2007-07-12
Dear Aaron,

But this is a really good news about the skype :) ! I have been out of country on trip for a while, did not have time to look around. In the end, i had to reinstall feisty and in order to avoid the situation with thunderbird 2 again, i just installed the older 1.5 version. I will try the thunderbird 1.5 with scim and let you know, as i remember in edgy it worked very well. I will try the new skype version asap, hopefully it'll  work, as we have something in common  - chatting with wifes in Chinese :) :)

---

### Post by atmartin50 on 2007-07-12
Damon: I upgraded to Feisty from Edgy a few weeks ago, and the export command worked fine for me. Just copy and paste the line from the instructions into the Terminal, and you should be all set. Thunderbird is opening and functioning smoothly for me, with the exception of my being unable to type Chinese.

tomash_cz: Yes, it is great news---I'm really happy with Skype 1.4 so far:). Be aware that I don't think you can get the Beta version for Edgy... I tried, and there's an audio dependency that's not met. As for T-bird, it's a bummer that I still can't type Chinese within the program, but I like version 2 too much to roll back to version 1.5; I'll just type any Chinese messages in the Gmail server. If you see any fixes for this issue, however, please let me know! Thanks.

---

