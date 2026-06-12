---
title: "hal Daemon"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by moondogie on 2008-01-10
I have lost all outside use of my system i.e. internet , usb ports .

I am now working off the Feisty Live cd to write this post . How do I go about enabling HAL I lost the hal daemon when I turned off the cups daemon and the d-buss daemon and here I am ! I have been loked out of the services in the GUI and I am not able to figure out how to restart hal in command line .I did go to the help files under Advanced , then to administration and I found the hald info and tried the debug process to no avail .
So I need some guidance .
What a mess .
Thanks Moondogie:(

---

### Post by theRightNee on 2008-01-11
wow...thats a doozie
worst case scenario=clean reinstall

i am sorry i cannot say more than that

---

### Post by moondogie on 2008-01-11
Thanks , The worst case scenario is what I want to avoid ! I have an external HD that I thought I could back up my files with as I am able to see my hard drive through the live cd but I can'r get permission to save files to the external drive. I thinks I'm screwed this time unless ....
Moondogie

---

### Post by ryanVickers on 2008-01-11
in recovery mode, it doesn't run by default.... I just went "hald" in the terminal... :rolleyes:

---

### Post by moondogie on 2008-01-11
Thanks , I tried that in terminal and got a blinking curser after hitting the return key .
So it won't start unless it's already there running if you know what I mean .The computer won't shut off unless I hit ctrl,alt, delete , actually it reboots so I have to do hard shut down .... Your hal daemon is performing correctly and mine is shut down and wont restart .
You can't think of another way to re-start the hald ?
Moondogie

---

### Post by ryanVickers on 2008-01-11
hm, if you run a task in the terminal, thats what will happpen - you will just not think it's running because theres no output, but if there was erros youd no and if it failed, youd know, but I think that worked then... when you quit the terminal though it kills it btw

---

### Post by buccaneere on 2008-01-11
Can you restart a process that forces hal to restart?

[HTML]sudo /etc/init.d/xxx restart[/HTML]

where 'xxx' is a hardware process...

---

