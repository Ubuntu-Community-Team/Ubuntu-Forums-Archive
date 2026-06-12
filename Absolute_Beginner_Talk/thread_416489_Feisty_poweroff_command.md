---
title: "Feisty poweroff command"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Kuoi on 2007-04-21
Hello ,

After the upgrade to Feisty Fawn , I have  just 1 issue that I can't solve.

I had a starter on my desktop with the following command

> sudo shutdown --poweroff 10:00
This made my computer poweroff at 10 a clock.

Now this command doesn't work anymore.

I've installed Gshutdown , but doesn't work either , or at least , ... it seems only to work when I'm very lucky.

Can somebody tell me what commands are used in Feisty , or why my starter doesn't work anymore ?

Many thanks in advance,  Kuoi

---

### Post by heimo on 2007-04-21
Try something like:
```
sudo shutdown -h 10:00 &
```

And if you want to cancel it:
```
sudo shutdown -c

```

---

### Post by GSF1200S on 2007-04-21
> **Kuoi said:**
> Hello ,

After the upgrade to Feisty Fawn , I have  just 1 issue that I can't solve.

I had a starter on my desktop with the following command


This made my computer poweroff at 10 a clock.

Now this command doesn't work anymore.

I've installed Gshutdown , but doesn't work either , or at least , ... it seems only to work when I'm very lucky.

Can somebody tell me what commands are used in Feisty , or why my starter doesn't work anymore ?

Many thanks in advance,  Kuoi

Wow.. I didnt even know this was possible! I would like to know how to do this.

I guess I would ask how you installed the shutdown program..  Maybe some of your dependencies arent with it and thats why its not working..

Hopefully somebody will respond to this...

---

### Post by heimo on 2007-04-21
> **GSF1200S said:**
> 
I guess I would ask how you installed the shutdown program.. 

No need to install it, it's there by default.

---

### Post by Kuoi on 2007-04-21
> **heimo said:**
> Try something like:
```
sudo shutdown -h 10:00 &
```

And if you want to cancel it:
```
sudo shutdown -c

```

Not working :confused:

---

### Post by Kuoi on 2007-04-21
> **GSF1200S said:**
> Wow.. I didnt even know this was possible! I would like to know how to do this.

I guess I would ask how you installed the shutdown program..  Maybe some of your dependencies arent with it and thats why its not working..

Hopefully somebody will respond to this...

If you mean the starter :

Just rightclick on an empty place on your desktop.
Then click on "add starter"
Type in the starter command as mentioned in my first message.
You have to change the time ( if needed ) , and I did is by rightclicking on the starter on the desktop , and changed the time.

If you mean Gshutdown , I've used synaptic to install it.

Kuoi

---

### Post by heimo on 2007-04-21
> **Kuoi said:**
> Not working :confused:

If you run it on a terminal, what does it say?

---

### Post by Kuoi on 2007-04-21
I've configured that if I let Gshutdown on "automatic" settings , and just edit the time , and select "turn off computer" , that my computer is "logging out" but not "turned off" .
So , the program is working , but it does "log out" my pc , instead of "power off" .

A bug in Kshutdown or do I have to change 1 or an other setting in Ubuntu ?

Kuoi

---

### Post by Kuoi on 2007-04-21
I've just made myself a new starter on the desktop , and now it's working well ( at least , it did once )  
:) 

BTW : If you make a new starter for this command , you have to change the "type" to ' terminal program' ( or how it's called in English , I use the Dutch version of Ubuntu )
The latest command I've used is > sudo shutdown -h 14:50

It should be a bit easier if GShutdown would work , but I'm fine with this command too.
And I wouldn't know about GShutdown ,  if my command wasn't broken in the first place .

Greetings , Kuoi

---

### Post by IainT on 2007-04-22
This is only a day old so I hope contributing to say 'me too' isn't out of line.

GShutdown worked fine in Dapper but now seems to just log me out.

---

### Post by ramjet_1953 on 2007-04-22
Hmmmm!

This is interesting!

I used Gshutdown on Edgy and it worked fine.

I downloaded the latest version from here: [http://gshutdown.tuxfamily.org/](http://gshutdown.tuxfamily.org/) and like you said, it doesn't work. 

All it did was take me back to the Log In Screen.

Not to be put-off I did a bit of investigating and discovered that the dependancies for Gshutdown are:

libgtk2.0-dev
libglade2-dev
libnotify-dev

The last two items are not installed in Feisty by default.

I then downloaded the tarball and compiled my own package, making sure all of the above dependancies were satisfied. It compiled and installed perfectly.

However when I ran it, the same problem was there, it just went back to the log in screen!

I guess you can't win them all!!!!

Regards,
Roger 8-)

---

### Post by MGStreak on 2007-04-24
I'm having the same problem... I'm only getting kicked to the login/out screen... despite the fact that I have automatic login enabled!  Meaning that right now, the ONLY time I see the login screen is when Gshutdown doesn't work (which, so far, has been every attempt I've made.)

Over here we are having the same problem... hopefully someone can help us out:
[http://ubuntuforums.org/showthread.php?p=2521820](http://ubuntuforums.org/showthread.php?p=2521820)

---

### Post by Cicatrix on 2007-04-24
I believe you need to add the parameter P to shutdown, so ti becomes "shutdown -hP". that was my problem some time ago, but the P tells it that you want to shut down completely for poweroff.

---

### Post by MGStreak on 2007-04-25
> **Cicatrix said:**
> I believe you need to add the parameter P to shutdown, so ti becomes "shutdown -hP". that was my problem some time ago, but the P tells it that you want to shut down completely for poweroff.

Hi there Cicatrix,

Thanks for the suggestion, but unfortunately, I just tried it out, and it was to no avail.  Still no shutdown, or even a 'log out' with the specified command!  At least the 'autodetect' option can kick me to the login screen... but unfortunately, the problem remains.

Anyone else (or Cicatrix, any other ideas?)
Thanks.

---

### Post by Cicatrix on 2007-04-25
I think I know why it isn't working: Ubuntu now uses Upstart instead of sysvinit. I guess Gshutdown shuts down GDM, and assumes that that will trigger the computer to shut down, but in fact, due to the new version of GDM and upstart, then they will try to keep the Desktop environment running, except if they get a specific shutdown command, which Gshutdown doesn't know how to use.

Possible solutions I can see are:
*Install sysVinit and use that instead of Upstart (slower startup and shutdown times).
or
*Notify the Gshutdown team of the missing compatibility with Upstart, and wait.

---

### Post by Kuoi on 2007-04-25
> **Cicatrix said:**
> I think I know why it isn't working: Ubuntu now uses Upstart instead of sysvinit. I guess Gshutdown shuts down GDM, and assumes that that will trigger the computer to shut down, but in fact, due to the new version of GDM and upstart, then they will try to keep the Desktop environment running, except if they get a specific shutdown command, which Gshutdown doesn't know how to use.

Possible solutions I can see are:
*Install sysVinit and use that instead of Upstart (slower startup and shutdown times).
or
*Notify the Gshutdown team of the missing compatibility with Upstart, and wait.

I've just send them a mail to notify them about the problem.
I've quoted your reply to them in the mail , with the hope they will understand what the exact problem is.
Hope you don't mind ?

Kuoi

---

### Post by Maxime81 on 2007-04-26
Hi,

I don't know when i'll can care about this bug. (I'm student... and very busy currently...)

But you can try to change the default command to sudo shutdown.
See the wiki :
[http://gshutdown.tuxfamily.org/en/wiki/doku.php?id=faq](http://gshutdown.tuxfamily.org/en/wiki/doku.php?id=faq)


Thank you for your bug report ^. And excuse my english ;).

Max (one of the 2 developers ;)).

---

### Post by Kuoi on 2007-04-26
Hello Max ,

Don't bother , school comes first , we all understand.
Many thanks in advance anyway.

And congratulations with this nice program you made , very well done .

I promise I start translate it ( or try anyway ) tomorrow.

Greetings , Kuoi

---

### Post by MGStreak on 2007-04-27
I think I can confirm the suspected problem; namely, that GDM has been changed from what GShutDown is normally calling upon.  I found an old suggestion on the GShutDown website suggesting a command line approach to running the program as root, and here was what the terminal spat out at me: 
(sorry I can't figure out how to post this in those fancy 'code' boxes... I'm new here)  :-}

gksu gshutdown
n.

(gshutdown:7216): Gtk-CRITICAL **: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed

(gshutdown:7216): Gtk-CRITICAL **: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
Metacity = GNOME !

** (gshutdown:7216): WARNING **: Failed to establish a connection with GDM: No such file or directory

Anyways, it seems to me that the last line in particular illustrates the issue.  Kuoi, perhaps you would be so kind to send this off to Max with the translation you are going to be sending?  Perhaps they might find it useful?

---

### Post by Kuoi on 2007-04-27
MGstreak ... well done !

I've send the message to Max , and let's hope it helps to figure out the problem.

About your > fancy code boxes problem ...

Before you'll write down the sentence you want in the box , you must click on the following button [Quote]("http://ubuntuforums.org/images/uf/editor/quote.gif") , and then start to type.

Greetings, Kuoi

---

### Post by MGStreak on 2007-04-27
Glad I could help... just trying to 'do my part' as it were.

and regarding the stupid boxes that I couldn't figure out:
> 
Thank you Kuoi!


Your post helped me understand what I was doing wrong!  So now I also figured out how to post messages in 

```

A CODE WINDOW!!! Yay!
Thanks again!

```

---

### Post by Kuoi on 2007-04-30
I've find a solution for an poweroff issue that works for me .
My computer didn't poweroff when I used the shutdown button.

For some poweroff issues this should be the solution I guess ...

**[Poweroff Solution ?]("http://ubuntuforums.org/showthread.php?t=428363")**

Greetings, Kuoi

---

