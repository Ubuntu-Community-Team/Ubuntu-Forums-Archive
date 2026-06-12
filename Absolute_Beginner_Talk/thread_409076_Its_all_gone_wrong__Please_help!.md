---
title: "Its all gone wrong / Please help!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-14
Hi from the live CD!

Ive recently attempted to amend the screen resolution size by amending the xorg/confg file, I then read via a linux forum that the entire config could be amended by running a command in terminal (sorry I really should have noted all this down!), the result was a bios style screen which allowed me to amend the xorg.....

Upon restarting xorg, it all went wrong, now I simply receive a bios style screen informing me that a fatal error occurred, I get to see the report, which indicates that no screen was located.

All is not lost.....I hope....I did backup the xorg file previously! however I am at a complete loss at how to replace the xorg file....after reading the report and selecting ok, I simpy have a blank screen where I may type...but nothing happens...

Man I knew I shouldnt have gone tinkering with things I have little understanding for.....can anyone help"?"

---

### Post by Lucifiel on 2007-04-14
Uhm... okay, I had a similar issue a few days ago where I accidentally deleted my default ATI drivers.

Not sure if it might work for you but I was told to try booting in "Recovery mode" from "Grub menu".

Then, at the command prompt, type "sudo dpkg-reconfigure xserver-xorg". I assume that by doing this, you can reset xorg.conf by selecting your graphics card and configuring your monitor settings. Also, note that when you are configuring your Monitor, make sure to select "Basic" mode. If you try "Advanced" mode, you could likely mess up your monitor settings!

---

### Post by TURNER on 2007-04-14
wow thanks for the quick response....how can I access the grub menu, as mentioned whilst booting xorg simply falls over...no options to enter any grub menu...

I am running from the live cd at the mo....can I access from here maybe?

---

### Post by mario_b on 2007-04-14
Does the blank screen where you can type look like a terminal?

In this case you can copy your backed up xorg.conf to /etc/X11

Do you know the directory where you saved your old xorg config file?

---

### Post by Lucifiel on 2007-04-14
> **TURNER said:**
> wow thanks for the quick response....how can I access the grub menu, as mentioned whilst booting xorg simply falls over...no options to enter any grub menu...

I am running from the live cd at the mo....can I access from here maybe?

Oh dear, you can't access the boot menu, eh? I'd assumed that you just couldn't boot into Ubuntu, my bad. :/

---

### Post by TURNER on 2007-04-14
> Does the blank screen where you can type look like a terminal?

In this case you can copy your backed up xorg.conf to /etc/X11

Do you know the directory where you saved your old xorg config file?

There isnt a terminal prompt, just a complete blank screen....the back up is also in etc/x11/xorg.confg

---

### Post by mario_b on 2007-04-14
When you are in the blank screen, can you switch to a console by pressing

ctrl-alt-F1

on the keyboard?

---

### Post by TURNER on 2007-04-14
> When you are in the blank screen, can you switch to a console by pressing

ctrl-alt-F1

on the keyboard?

I havent tried this, I will need to log out and give it a shot....if it does work can I swop over to the backup with

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

?

---

### Post by mario_b on 2007-04-14
Yes, that' right

---

### Post by TURNER on 2007-04-14
ok...iam off to give it a try.

hopefully I will be able to report back from my main boot, and not the live cd!

I would apprecite it if you could keep an eye on this thread incase this doesnt resolve it!!:confused: 

thanks for your help so far :D

---

### Post by mario_b on 2007-04-14
Ok.

Just one more thing:

when you access the console, before giving the cp command, you have to login with your username and pwd

---

### Post by TURNER on 2007-04-14
>  Ok.

Just one more thing:

when you access the console, before giving the cp command, you have to login with your username and pwd

It worked!

I am now back in on my installed Ubuntu....thanks a million!

Now for the clean up....does this mean that the bad settings are now contained on the xorg.conf_backup file, or is the back_up file now the main xorg settings file?

Basically I'd like to delete the bad file, and create a new backup...

---

### Post by Lucifiel on 2007-04-14
> **TURNER said:**
> It worked!

I am now back in on my installed Ubuntu....thanks a million!

Now for the clean up....does this mean that the bad settings are now contained on the xorg.conf_backup file, or is the back_up file now the main xorg settings file?

Basically I'd like to delete the bad file, and create a new backup...

Whew... congrats! :D :popcorn: 

It's always a relief to come back into Ubuntu, eh? :P

---

### Post by TURNER on 2007-04-14
> It's always a relief to come back into Ubuntu, eh? :P

Definitely! It's like coming home all over...:D 

It's a massive relief since theres English football action on quite soon :-P

Thanks again for all your help....this type of support is what makes this OS so sweet!:D

---

### Post by mario_b on 2007-04-14
> **TURNER said:**
> 
Now for the clean up....does this mean that the bad settings are now contained on the xorg.conf_backup file, or is the back_up file now the main xorg settings file?


If you did this:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

then the old xorg.conf with the bad settings is gone. Now both xorg.conf_backup and xorg.conf contain the working config

> **TURNER said:**
> 
I am now back in on my installed Ubuntu....thanks a million!

You are welcome :-)

---

### Post by TURNER on 2007-04-14
> If you did this:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

then the old xorg.conf with the bad settings is gone. Now both xorg.conf_backup and xorg.conf contain the working config

Thats exactly what I did....thanks again mate! :D

---

### Post by Lucifiel on 2007-04-14
> **TURNER said:**
> Definitely! It's like coming home all over...:D 

It's a massive relief since theres English football action on quite soon :-P

Thanks again for all your help....this type of support is what makes this OS so sweet!:D

Heh, I switched to Ubuntu less than 2 weeks ago and now I'm fully hooked. :) 

The only things I miss are the very neat themes Windows XP has like the ones by StudioTwenty Eight.

---

### Post by TURNER on 2007-04-14
> The only things I miss are the very neat themes Windows XP has like the ones by StudioTwenty Eight.

Really...I think linux is superior to Wi***ws with regards visual display.

Have you checked out the themes available via gnome look.org, assuming you are using gnome?

---

### Post by Lucifiel on 2007-04-14
> **TURNER said:**
> Really...I think linux is superior to Wi***ws with regards visual display.

Have you checked out the themes available via gnome look.org, assuming you are using gnome?

Yeah but I don't really most of them. :p

I prefer smooth, sleek and slimmed-down themes. Still looking, though for something like this. :)

[http://www.deviantart.com/deviation/7449129/](http://www.deviantart.com/deviation/7449129/)

---

### Post by TURNER on 2007-04-14
> Yeah but I don't really most of them.

I prefer smooth, sleek and slimmed-down themes. Still looking, though for something like this.

[http://www.deviantart.com/deviation/7449129/](http://www.deviantart.com/deviation/7449129/)

The screen shot looks really cool...I am pretty sure with a little playing around you could achieve the same as that in Ubuntu, perhaps starting with a dock, cairo dock or something similar? 

Or perhaps KDE would be more suited to your display needs??

I'll take a look around at themes, I am usually looking around anyway, still trying to set up the perfect desktop myself :D  If I find something would you like me to pm you here?

---

### Post by Lucifiel on 2007-04-14
> **TURNER said:**
> The screen shot looks really cool...I am pretty sure with a little playing around you could achieve the same as that in Ubuntu, perhaps starting with a dock, cairo dock or something similar? 

Or perhaps KDE would be more suited to your display needs??

I'll take a look around at themes, I am usually looking around anyway, still trying to set up the perfect desktop myself :D  If I find something would you like me to pm you here?

Oh sure, thank you! :D Yeah, you're right. I need to spend some time learning about this stuff as I'm still new to Ubuntu. :) 

Hell yeah, I've been looking around. And so far, only Blended comes 3/4 close in terms of "coolness" but I'm still trying to learn how to install the theme. 

[http://gnome-look.org/content/show.php/Blended+%284+Compiz%29?content=43760](http://gnome-look.org/content/show.php/Blended+%284+Compiz%29?content=43760)

---

