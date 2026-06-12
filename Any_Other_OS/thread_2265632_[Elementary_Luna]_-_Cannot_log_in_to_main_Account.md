---
title: "[Elementary Luna] - Cannot log in to main Account"
date: 2015-02-16
forum: Any Other OS
---

### Post by j-desanto0 on 2015-02-16
Once again, my apologizes for all the requests for aid. Another quick search found me nothing I could understand for this issue. 

Earlier today after fixing my previous issues I restarted my system. Unfortunately I forgot that the Deepin install USB was plugged in and it somehow screwed up my boot. So after fixing this I restart and no matter if I boot into normal or recovery for Elementary it asks me for my password. During install I set it up for automatic log-in so this is odd to start off. After I type in my password the screen goes dark for a few moments before going back to the log in screen. 

I can access a guest session and even work in the terminal and get applications from software manager with my password. The only thing I cannot do is log into my named account. 

Anyone have any ideas for fixing this?

---

### Post by kerry_s on 2015-02-16
did you check to see if you got the correct session selected before you try logging in ? it's been a while since i played with elementary, but i think the selection appears after you select your user, right next to the okay should be a little gear looking icon.

---

### Post by j-desanto0 on 2015-02-16
> **kerry_s said:**
> did you check to see if you got the correct session selected before you try logging in ? it's been a while since i played with elementary, but i think the selection appears after you select your user, right next to the okay should be a little gear looking icon.

No gear that I can see. Just the log in box with my picture and the password entry box.

---

### Post by kerry_s on 2015-02-16
how about the panel on the top ?
maybe it's time for you to update to the next version, it's at beta 2, but was very good when i tried it last.
[https://elementaryos.org/journal/freya-beta-1-available-for-developers-testers](https://elementaryos.org/journal/freya-beta-1-available-for-developers-testers)

---

### Post by j-desanto0 on 2015-02-16
> **kerry_s said:**
> how about the panel on the top ?

Unforunately not. The top panel has the virtual keyboard, the sound control and the restart/shut down button.

---

### Post by Bashing-om on 2015-02-16
j-desanto0; Hello:

> 
 After I type in my password the screen goes dark for a few moments before going back to the log in screen. 

Have you lost authorization to access "your" desktop ?
What returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
And we see who is authorized.

security
[INDENT][INDENT]controlled access, controlled permissions
[/INDENT][/INDENT]

---

### Post by j-desanto0 on 2015-02-16
> **Bashing-om said:**
> j-desanto0; Hello:


Have you lost authorization to access "your" desktop ?
What returns:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
And we see who is authorized.

security[INDENT][INDENT]controlled access, controlled permissions
[/INDENT]
[/INDENT]


Forgive me, do I type that into the terminal?

---

### Post by Bashing-om on 2015-02-16
j-desanto0; Hey;

My apologies for my assumptions. Yes in terminal: (ctl+alt+F1 at the login screen);
Post these outputs back here to the forum - Between code tags, please:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

No problem, we understand
[INDENT][INDENT][INDENT]got to learn somewhere
[/INDENT][/INDENT][/INDENT]

---

### Post by j-desanto0 on 2015-02-16
Thank you, Bashing-om; 

```

-rw------- 1 root 0 Feb 16 13:58 .Xauthority
ls: cannot access .ICEauthority: No such file or directory
drwxr-xr-x  3 root root 4096 Feb 16 13:37 .
drwxr-xr-x 23 root root 4096 Feb 16 13:38 ..
drwxr-xr-x  4 root root 4096 Feb 16 18:33 josh

```

I hope I did it right. Thanks you for all the help so far.


> **Bashing-om said:**
> j-desanto0; Hey;

My apologies for my assumptions. Yes in terminal: (ctl+alt+F1 at the login screen);
Post these outputs back here to the forum - Between code tags, please:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

No problem, we understand[INDENT][INDENT][INDENT]got to learn somewhere
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2015-02-16
j-desanto0; Humm ..

Try again:
```

ls -al .ICEauthority

```
That file should exist.

And suspicion confirmed that "you" do not have the authority to access the GUI.
per:
> 
-rw------- 1 root 0 Feb 16 13:58 .Xauthority
drwxr-xr-x  4 root root 4096 Feb 16 18:33 josh

should be similar as mine:
```

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 652 Feb 16 11:25 .ICEauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Feb  1 11:38 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 Feb 16 11:25 sysop
sysop@1404mini:~$

```
where my 'username' is sysop. you should see 'josh'

Once we know what is going on with .ICEauthority we will fix the access so 'you', josh, have the authorization to access your /home.

[INDENT][INDENT]no big deal ( we hope ) [/INDENT][/INDENT]

---

### Post by j-desanto0 on 2015-02-16
Bashing-om;

Thanks again for the help.

attempted 
```

ls -al .ICEauthority

```

again and received the same response. I wish I could copy paste from your code quote but after getting in VIA ctrl+alt+f1 I have to manually type everything.

> **Bashing-om said:**
> j-desanto0; Humm ..

Try again:
```

ls -al .ICEauthority

```
That file should exist.

And suspicion confirmed that "you" do not have the authority to access the GUI.
per:

should be similar as mine:
```

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 652 Feb 16 11:25 .ICEauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Feb  1 11:38 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 Feb 16 11:25 sysop
sysop@1404mini:~$

```
where my 'username' is sysop. you should see 'josh'

Once we know what is going on with .ICEauthority we will fix the access so 'you', josh, have the authorization to access your /home.
[INDENT][INDENT]no big deal ( we hope ) [/INDENT]
[/INDENT]


---

### Post by j-desanto0 on 2015-02-16
> **kerry_s said:**
> how about the panel on the top ?
maybe it's time for you to update to the next version, it's at beta 2, but was very good when i tried it last.
[https://elementaryos.org/journal/freya-beta-1-available-for-developers-testers](https://elementaryos.org/journal/freya-beta-1-available-for-developers-testers)

I don't know if something is wrong with my unetbootin on my ancient Ubuntu laptop or if it is something else but the install failed ... created the partition but didn't install.

---

### Post by Bashing-om on 2015-02-16
j-desanto0' ???

> 
I don't know if something is wrong with my unetbootin on my ancient Ubuntu laptop or if it is something else but the install failed ... created the partition but didn't install.


Is regaining access to your GUI now a moot point ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by j-desanto0 on 2015-02-16
Bashing-om;

No regaining control of the GUI is the main priorty. I attempted Kerry's solution before I saw your original response and just didn't want to seem rude by not replying to him.

> **Bashing-om said:**
> j-desanto0' ???



Is regaining access to your GUI now a moot point ?
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


---

### Post by kerry_s on 2015-02-16
i'm going to let you 2 handle it, as i'm out of ideas & on my way out the door. sorry other things to do, 3 kids to feed, need food. lol

---

### Post by Bashing-om on 2015-02-16
j-desanto0; Ho Kay !


Let's give this a whirl,

```

touch .ICEauthority
sudo chown josh:josh .ICEauthority
chmod 600 .ICEauthority
sudo chown josh:josh .Xauthority
sudo chown josh:josh /home/josh
sudo chmod -R a+rwX,o-w /home/$USER

```
If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

reboot, and let's see the effect. Now you boot to the GUI .
betcha.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by j-desanto0 on 2015-02-17
Morning, Bashing-om;

That worked! I was able to get in to my session this morning and have restarted several times to make sure everything stayed good.

Thanks you were an amazing help!


> **Bashing-om said:**
> j-desanto0; Ho Kay !


Let's give this a whirl,

```

touch .ICEauthority
sudo chown josh:josh .ICEauthority
chmod 600 .ICEauthority
sudo chown josh:josh .Xauthority
sudo chown josh:josh /home/josh
sudo chmod -R a+rwX,o-w /home/$USER

```
If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

reboot, and let's see the effect. Now you boot to the GUI .
betcha.
[INDENT][INDENT]hey, it could happen
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2015-02-17
j-desanto0; Out standing !

Pleased to be of some help. Hope this little matter makes you the more comfortable with this - 
our operating system by choice .

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

