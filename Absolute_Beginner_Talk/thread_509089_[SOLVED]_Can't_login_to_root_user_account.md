---
title: "[SOLVED] Can't login to root user account?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-07-25
I can't login to the root user account.Password is not working.But while installing I created an acoount which use.Except that I can't remember that I provided any other password.What is the problem ?Is there any default password?

---

### Post by Raineer on 2007-07-25
Ubuntu does not have a "root" account.  If you wish to have root access, there are several things you can do.

For root access to a single command it's:
```
sudo typecommandhere
```
followed by *your* user password at the Password:  prompt.

For root access consistently at a terminal enter:
```
sudo -i
```
followed by your user password.

For GUI root access, you can press Alt-F2 and enter 
```
gksudo nautilius
```
for a root-based nautilius browser, etc

Actually using your computer as root is a bad idea (one I **always** was guilty of while running Redhat). Ubuntu is brilliant by not allowing this.

---

### Post by aysiu on 2007-07-25
Why do you want to log in as root?

Tell us what you're trying to accomplish, and we'll tell you the best way to accomplish it. And you will not have to log in as root to do so.

---

### Post by chatterjee on 2007-07-25
I know it's a bad idea coz that makes the OS more vulnerable.I just wanted to see how to do it.In System>Administration>User and Groups I find an account named /root.Can't it be called root account?BTW,thanks for you help.:)

---

### Post by Raineer on 2007-07-25
To answer your question most directly, no it cannot be done.  This was also a small "hiccup" for me when I migrated to Ubuntu as I didn't quite understand how it worked.  You do not log in as "root", and the ability is not present as it was not written that way.

---

### Post by gimpguy2000 on 2007-07-25
Funny, I was about to ask the same thing then ran across this. I have broken links to delete but even when I go into Root \user mode, any root, I get denied. It asks for password but when I put it in, it's denied. 

 Paul

---

### Post by amac777 on 2007-07-25
It may be a bad idea, but....  *YES*, of course it *CAN* be done.

To enable root logins, just set up a password for root:

```
passwd root
```

Then you can login to your computer with the user root and that password.
Hope this helps

EDIT: Once you realize that you don't need root login on Ubuntu, you can lock up the root account again by using:

```
passwd -l root
```

---

### Post by gimpguy2000 on 2007-07-25
> **amac777 said:**
> It may be a bad idea, but....  *YES*, of course it *CAN* be done.

To enable root logins, just set up a password for root:

```
passwd root
```

Then you can login to your computer with the user root and that password.
Hope this helps.


Heyyy, thanks, it worked. I just wanted to add though , "and I must be actually learning"

```
sudo passwd root
``` is what worked for me. 

Just to note: any open source OS I can't get root access to, I won't have. Whether safe or not, I believe it's right, else it would be Windows. So** thanks**, you just saved me from posting goodbye to Ubuntu and going back to Fedora. :guitar::popcorn:

 Cheers,

 Paul

Did I mention, THANKS? two thumbs up!

---

### Post by KeitaroCoS on 2007-07-25
hey, I want to edit my sources.list file for the Compiz fusion thing, and I can't because I don't have permission to do so, any ideas?

---

### Post by amac777 on 2007-07-25
> **gimpguy2000 said:**
> Heyyy, thanks, it worked. I just wanted to add though , "and I must be actually learning"

```
sudo passwd root
``` is what worked for me. 

Just to note: any open source OS I can't get root access to, I won't have. Whether safe or not, I believe it's right, else it would be Windows. So** thanks**, you just saved me from posting goodbye to Ubuntu and going back to Fedora. :guitar::popcorn:

Haha, no problem. Because you figured out my riddle (actually, it was an unintentional omission of the word sudo), you actually figured out why you don't need to login as root in the first place. :) Specifically: All commands needing root access can be done from your user's account by prefixing them with 'sudo'. But choices and freedoms to do things in your own way are important too.

---

### Post by amac777 on 2007-07-25
> **KeitaroCoS said:**
> hey, I want to edit my sources.list file for the Compiz fusion thing, and I can't because I don't have permission to do so, any ideas?

Try:

```
sudo nano /etc/apt/sources.list
```


or instead of nano you can use gedit or vi or your favorite text editor.

---

### Post by kvonb on 2007-07-25
> **KeitaroCoS said:**
> hey, I want to edit my sources.list file for the Compiz fusion thing, and I can't because I don't have permission to do so, any ideas?

Haven't you read what's been written above?

Anyway, you don't need to do that, simply select "Software Sources" from the System->Administration menu, select the "Third Party Sources" tab and add it in there.

And your next post will be a "help I can't get into my desktop" sort of thing!

I don't mean to be rude, but if you don't know how to add a line to your sources.list file, you really shouldn't be messing with Compiz fusion!  It is highly unstable and will most likely stuff your desktop up!

It's kind of like: "I don't know how to drive a car, but I want to add a supercharger and Nitrous kit first!" :).

Just make sure you read a lot of threads on it before you take the plunge, it might give you some insight on how to recover from possible problems.

---

### Post by chatterjee on 2007-07-25
> sudo passwd root gave a successful password setting report after using it in terminal but when I tried to get into the root account by 'switch user' it gives "System administrator is not allowed to login from this page".From which page then?

---

### Post by amac777 on 2007-07-25
> **chatterjee said:**
> gave a successful password setting report after using it in terminal but when I tried to get into the root account by 'switch user' it gives "System administrator is not allowed to login from this page".From which page then?

```
ssh root@localhost
```

Should allow you to login as root.

If you want to login as root from the graphical login screens (like from the switch user screen), then you will need to enable root logins from the GUI. I'm not in front of my ubuntu box right now, but you will need to do something like this:

1: Click on System -> Administration -> Login Screen Setup -> Security tab
2: Put a check by Allow root to login with GDM
3: Logout (or switch users) and type root for username and in the password field whatever your root password is.

Hope this helps.

---

### Post by gimpguy2000 on 2007-07-25
> **amac777 said:**
> Haha, no problem. Because you figured out my riddle (actually, it was an unintentional omission of the word sudo), you actually figured out why you don't need to login as root in the first place. :) Specifically: All commands needing root access can be done from your user's account by prefixing them with 'sudo'. But choices and freedoms to do things in your own way are important too.

 LOL, sorry for the late reply, I had to do a reinstall. Somehow my ubuntu when I installed KDE, went to Kubuntu and wouldn't let loose. So I reinstalled. Ah, I see the point in the root access now ;)

 Thanks again,

 the riddler :)

---

### Post by aysiu on 2007-07-25
> **chatterjee said:**
> gave a successful password setting report after using it in terminal but when I tried to get into the root account by 'switch user' it gives "System administrator is not allowed to login from this page".From which page then?
Read this and save yourself some trouble:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by chatterjee on 2007-07-27
Thank you all my friends,but it was amac77's suggestion which worked for me!Thanks again!

---

