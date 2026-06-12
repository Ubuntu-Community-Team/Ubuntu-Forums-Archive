---
title: "[SOLVED] Rebooting through command line?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-11-11
I remember reading in the forum once that you can reboot by typing something in the terminal and that it basically starts everything up again without actually having to reboot your computer.

For the life of me, I can't find that thread again.

Can someone please tell me what you can type into terminal to reboot your machine in the even you wanted to see if drives are being seen after editing fstab.

Thanks in advance...

---

### Post by Nano Geek on 2007-11-11
Well, to re-mount all hard drives, you just run this:```
sudo mount -a
```

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-11
it's not clean at all and you loses all unsaved data but alt-ctrl-back space restartes the x11 server and most of the apps you have running
then there is 
sudo shutdown -r now    --- i think ? man have to do a man shutdown to get the right sintax 
but this will accualy shut every thing down 
then if your computer frezzes and you have tried restarting x11 there is the 
"rasing pink elifants is uterly boring"
whitch is not that good but better then holding the power butten in 
and i cant do it justus if i explan it here sooo i gess google the pink elifents thingy ;)

---

### Post by mdpalow on 2007-11-12
thanks asjdfwejqrfjcvm msz34rq33,

I will try that shortly. Copying a lot of files from HD to HD and don't want to take a chance. However, what if you were editing xorg.conf for instance and wanted to reboot your system so you could see the results of that?

Thanks for your quick reply....

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
save the conf fig file and press alt-ctrl-back space

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **mdpalow said:**
> thanks asjdfwejqrfjcvm msz34rq33,

I will try that shortly. Copying a lot of files from HD to HD and don't want to take a chance. However, what if you were editing xorg.conf for instance and wanted to reboot your system so you could see the results of that?

Thanks for your quick reply....

to be more clear your when you edit the xorg.conf file your messing with the way x11 is configured so 
save the config and restart x11 by pressing alt-ctrl-backspace on kebord at same time 

the other guys comand is to remount your file systems --- can think of many uses but not what your looking for

---

### Post by Nano Geek on 2007-11-12
nvm

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> nvm

lol i didnt mean any disrespect

---

### Post by Nano Geek on 2007-11-12
> **mdpalow said:**
> thanks asjdfwejqrfjcvm msz34rq33,

I will try that shortly. Copying a lot of files from HD to HD and don't want to take a chance. However, what if you were editing xorg.conf for instance and wanted to reboot your system so you could see the results of that?

Thanks for your quick reply....Yes, what << joe >> said. Just type **CTRL+ALT+Backspace**.

---

### Post by Nano Geek on 2007-11-12
> **<<joe>> said:**
> lol i didnt mean any disrespectNo, I didn't mean you, I just said something but then I found out I was wrong.

---

### Post by mdpalow on 2007-11-12
thank you all on the "CTRL+ALT+Backspace."

Now just one more question... this one will test you. :)

how would you enter "CTRL+ALT+Backspace" in a terminal window IF you wanted a - SCRIPT - to do this for you automatically?

Thanks....

---

### Post by Nano Geek on 2007-11-12
Try this:```
sudo /etc/init.d/x11-common stop
```

---

### Post by akiratheoni on 2007-11-12
> **mdpalow said:**
> thank you all on the "CTRL+ALT+Backspace."

Now just one more question... this one will test you. :)

how would you enter "CTRL+ALT+Backspace" in a terminal window IF you wanted a - SCRIPT - to do this for you automatically?

Thanks....

I think it might be (If you're using GNOME or maybe Xfce):

```
sudo /etc/init.d/gdm stop
```

To start X:

```
sudo /etc/init.d/gdm start
```

I think that might be it. Someone correct me if I'm wrong.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **mdpalow said:**
> thank you all on the "CTRL+ALT+Backspace."

Now just one more question... this one will test you. :)

how would you enter "CTRL+ALT+Backspace" in a terminal window IF you wanted a - SCRIPT - to do this for you automatically?

Thanks....

haha crap lol 
i dont know

well i can gess when you press the CTRL+ALT+Backspace you are sending the kill singnal to the x11 server witch is really just a program running on your pc just like  any thing else but dont rember how to do it on command line :/ but i know you can lol give me a min

---

### Post by Nano Geek on 2007-11-12
> **akiratheoni said:**
> I think it might be (If you're using GNOME or maybe Xfce):

```
sudo /etc/init.d/gdm stop
```To start X:

```
sudo /etc/init.d/gdm start
```I think that might be it. Someone correct me if I'm wrong.Oh of course. You're right. I failed the test. :(

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
well they beat me to it :) but i was thinking something like that you may even wanna try a restart insted of stop but i thnk ubuntu forces the x11 server to start if it stops

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **akiratheoni said:**
> I think it might be (If you're using GNOME or maybe Xfce):

```
sudo /etc/init.d/gdm stop
```

To start X:

```
sudo /etc/init.d/gdm start
```

I think that might be it. Someone correct me if I'm wrong.

will this stop the x11 server as well ?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> Try this:```
sudo /etc/init.d/x11-common stop
```

i thought this would do it ??

---

### Post by akiratheoni on 2007-11-12
> **<<joe>> said:**
> will this stop the x11 server as well ?

AFAIK, yeah, it stops it and returns you to a text login screen. To start X again you log in then use the other command I gave you.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
k

---

### Post by mdpalow on 2007-11-12
K, I tried:

sudo /etc/init.d/gdm stop

and it went to black screen and then just locked.... no re-login or anything.... had to reboot.

any suggestions?

---

### Post by mdpalow on 2007-11-12
I also just tried:

sudo /etc/init.d/x11-common stop

nothing appeared to happen; was just brought to prompt again.

I then put in sudo /etc/init.d/x11-common start

and again just prompt appeared again. Did anything actually happen????

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
you have to sign back in then do it i gess thats what they said ??

---

### Post by mdpalow on 2007-11-12
right, understood I had to log back in, BUT... after doing "sudo /etc/init.d/gdm stop" it just locked up and didn't give me the option to log in again...Had to reboot.

the other commands I tried didn't appear to do anything...

Thanks...

---

### Post by robinl on 2007-11-12
It's actually /etc/init.d/gdm restart , but you can do it in a two step process. Once you issued /etc/init.d/gdm stop , you have to press ctrl+alt+F1 , login, and type in /etc/init.d/gdm start , and it should bring you back to the login screen. If not, try pressing ctrl+alt+F7-9 to go back to the X workspace.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **robinl said:**
> It's actually /etc/init.d/gdm restart , but you can do it in a two step process. Once you issued /etc/init.d/gdm stop , you have to press ctrl+alt+F1 , login, and type in /etc/init.d/gdm start , and it should bring you back to the login screen. If not, try pressing ctrl+alt+F7-9 to go back to the X workspace.

his goal is to have a script do it so that will not work right

---

### Post by mkoehler on 2007-11-12
As robinl said, it is actually 

```
sudo /etc/init.d/gdm restart
```

or

```
sudo /etc/init.d/kdm restart
```

based on the desktop environment that you are using.  CTRL+ALT+F# is, as you will find, a very useful command.  CTRL + ALT + F1 brings up your tty1 prompt, CTRL+ALT+F2 brings up your tty2 prompt.....CTRL + ALT + F7 brings up your standard X display (which happens to coincide with the tty7 prompt).  The tty prompts become especially useful when you mess up a setting in your xorg.conf file and X is unable to start, but it has many other uses as well.

Cheers!

---

