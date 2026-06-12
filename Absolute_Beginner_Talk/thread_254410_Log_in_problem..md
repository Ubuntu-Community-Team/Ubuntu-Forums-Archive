---
title: "Log in problem."
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Jimit87 on 2006-09-09
How do i log in as root?
when i was installing i had to make a username and password. just once. 

and i found out that i wasn't logged in as root by doing that.

what should i do?

EXPLAINE.

Thank you.

---

### Post by ChadMMc on 2006-09-09
Ubuntu doesn't really have a root, per se, but you being the user who installed the system has the ability to do administrative (root) tasks at anytime. when you open an administrative app (like synaptic, etc...) you just put in the password that you had put in at installation.

Hopwe this helps. :)

---

### Post by grey1 on 2006-09-20
> **ChadMMc said:**
> Ubuntu doesn't really have a root, per se, but you being the user who installed the system has the ability to do administrative (root) tasks at anytime. when you open an administrative app (like synaptic, etc...) you just put in the password that you had put in at installation.

Hopwe this helps. :)

I have a lil different problem.
This laptop came allready loaded with Ubunto 6.06, new, and when I try to load or change anything the lil happy box pops up [COLOR="Red"]Enter your password to perform administrative tasks[/COLOR] How do I find out what the password is or was or ? ? ?  

grey1

---

### Post by LotsOfPhil on 2006-09-20
Try the password that you use to login. If that doesn't work, try the passwords for other users' accounts (if there are any).

---

### Post by cello_dude90 on 2006-09-20
there is a very simple solution. just login to any account and then start a console. type in: sudo passwd root

then set a new password for the root user. go see this website below [http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME)

---

### Post by grey1 on 2006-09-20
I have tryed every password I have used on this laptop, even the password for this forum, with no luck at all.
I am the only user of this laptop since I got if FedEx. Very Frustrating.

---

### Post by LotsOfPhil on 2006-09-20
> **cello_dude90 said:**
> there is a very simple solution. just login to any account and then start a console. type in: sudo passwd root

then set a new password for the root user. go see this website below [http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME)
I don't see how this will help. The password for sudo is the same one that he doesn't know for his administrative tasks.

It looks like it can be distilled as "I don't know my root password, what do I do?"

---

### Post by dhruv_1884 on 2006-09-20
dude prepend the command with sudo
life if u wanna gedit tou sources list u need to type

```
sudo gedit /etc/apt/sources.list
```

to be root u need to use the sudo prepend

---

### Post by nickpaton on 2006-09-20
> **grey1 said:**
> I have tryed every password I have used on this laptop, even the password for this forum, with no luck at all.
I am the only user of this laptop since I got if FedEx. Very Frustrating.

To find the password you specified when you first set up the laptop:

restart the laptop in recovery mode.

At the prompt:

```
cd /home
```

Changes you into your home folder.

```
ls
```

The figure / name underneath will be the specified password (mine was in blue).

Close the laptop using CTR>ALT>DEL keys.

Restart - test out the password in a terminal with a sudo command.

---

### Post by grey1 on 2006-09-20
> **cello_dude90 said:**
> there is a very simple solution. just login to any account and then start a console. type in: sudo passwd root


then set a new password for the root user. go see this website below [http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_allow_root_user_to_login_into_GNOME)


  
1)  I login to any account and then start a console. I type in: sudo passwd root 
when I try to type a new password for the root user nothing happens, nothing shows,
as if the keyboard is not working.:confused: 

2)  When I go to Applications> - System tools> -  Root Terminal      

It wants a Password 

I must be doing somthing very wrong :confused:

---

### Post by nickpaton on 2006-09-20
Grey1 - can I suggest you try my suggestion.  I reread your first post, and this should tell you the password of the original person who set up Ubuntu on the laptop.

After closing and restarting use the sudo passwd root and enter the password you found.

Note that when you type it in after the password prompt, the cursor does not move, or register that you have not even typed anything in.

If everything is OK, after hitting enter:

```
Enter new UNIX password:
``` 

And so on.

---

### Post by grey1 on 2006-09-20
> **nickpaton said:**
> To find the password you specified when you first set up the laptop:

restart the laptop in recovery mode.

At the prompt:

```
cd /home
```

Changes you into your home folder.

```
ls
```

The figure / name underneath will be the specified password (mine was in blue).

Close the laptop using CTR>ALT>DEL keys.

Restart - test out the password in a terminal with a sudo command.

I did not set up the laptop. I purchased it off 
the internet allready loaded with 6.06 and
ready to run, "Linux Certified". I did no set 
up. 
When restarting the laptop in recovery mode.
the only prompt I get is - "Type Controle D to contenue". It will not except anything else.  :confused:

---

### Post by nickpaton on 2006-09-20
I completely understand your problem now - sorry for being slow!

I'm not sure what the solution is, since if you can get into the recovery console, you will be as root, and can then find out the password.

What happens when you do the CTRL>D keys?  What screen do you then have?

---

### Post by xpod on 2006-09-20
> I completely understand your problem now - sorry for being slow!

I'm not sure what the solution is,

MMMMMMM????
Strange statement?[-X

---

### Post by nickpaton on 2006-09-20
> **xpod said:**
> MMMMMMM????
Strange statement?[-X

Who are YOU calling strange???!!!!:grin:

---

### Post by xpod on 2006-09-20
SO your a "statement" now are you?:KS

EDIT:..Just get the chap logged on and dont get me going!!

---

### Post by nickpaton on 2006-09-20
> **grey1 said:**
> I did not set up the laptop. I purchased it off 
the internet allready loaded with 6.06 and
ready to run, "Linux Certified". I did no set 
up. 

Can you contact the seller to get the password?

I'm searching through posts for lost password, and you need to be in root
and recovery mode to get it, it seems.

I have found this thanks to 23Meg and post 1523710

> Boot with a live CD, mount your Ubuntu partition and navigate to your /home folder where your user will have self titled folder.

It does require downloading a Live CD; the other thing that occured to me was to simply do a reinstall.

...After a lot more searching, all that is coming back is into recovery mode as root and as I said earlier.

May I suggest that you make another post stating you have Control D to Continue rather than the 'traditional' boot screen, which includes choosing the recovery screen.
In other words how can you alter Grub with no password to amend it to add a recovery mode selection?

---

### Post by grey1 on 2006-09-20
> **nickpaton said:**
> Can you contact the seller to get the password?

I'm searching through posts for lost password, and you need to be in root
and recovery mode to get it, it seems.

I have found this thanks to 23Meg and post 1523710



It does require downloading a Live CD; the other thing that occured to me was to simply do a reinstall.

...After a lot more searching, all that is coming back is into recovery mode as root and as I said earlier.

May I suggest that you make another post stating you have Control D to Continue rather than the 'traditional' boot screen, which includes choosing the recovery screen.
In other words how can you alter Grub with no password to amend it to add a recovery mode selection?


Tried calling them and all I got was a man that
talked with a very heavy accsent that I could
not understand and real fastso got no where there, 
emailed them 5 or 6 timesand got no email back.
Would doing a reinstall delete bookmarks or any
other programed into this laptop ? ?

---

### Post by cello_dude90 on 2006-09-20
it should work since i can do it on my computer. unless you already have one set up and you dont remember what you entered. ill post a screen shot so you can see what it should read.This has to be typed in exactly like i have it typed in.

xxx@xxx:~$ sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

---

### Post by cello_dude90 on 2006-09-20
you'll have to go to Applications, Accesories, Terminal and use that with the command: sudo passwd root

---

### Post by nickpaton on 2006-09-21
> **cello_dude90 said:**
> you'll have to go to Applications, Accesories, Terminal and use that with the command: sudo passwd root

The problem with that is that you still need a password before you can progress on!!!

---

### Post by nickpaton on 2006-09-21
> **grey1 said:**
> Would doing a reinstall delete bookmarks or any
other programed into this laptop ? ?

In short everything will be lost if you simply do a reinstallk, but you can save your documents wherever you have saved them, and copy onto a CD.

Re your bookmarks, I assume you are using Firefox?

Within Firefox go into Bookmarks>Manage Bookmarks>File>Export..., and export them to a file in your home folder.

To restore simply reverse the process but import from...

Emails: To transfer all your boxes if you are using Thunderbird.  
Unhide hidden files in your home folder.
Go to /home/yourname/.mozilla-thunderbird/8q6itqlh.default (something like that!)/Mail

Copy all the folders inside there which are your boxes for your existing account(s).

To restore create a dummy account, which will create the .mozilla-thunderbird folder, and then simply paste over the folder inside there.

Sorry I cannot come up with something else to rescue your password but unless someone with a lot more knowledge can come up with a backdoor way to get in, I think you've had it.

---

