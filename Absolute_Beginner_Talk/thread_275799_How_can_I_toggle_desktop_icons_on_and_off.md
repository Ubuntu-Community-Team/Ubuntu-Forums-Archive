---
title: "How can I toggle desktop icons on and off?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by BackInTimeMan on 2006-10-11
I'd like to be able to hide/show my desktop icons. Is there a command I could put in a launcher that will do this?

---

### Post by BatteryCell on 2006-10-11
If by desktop icons you mean .desktop files than simply open them with a text editor and you should get something like:
```

[Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Hidden=false
Icon=trashcan_full
Name=Trash
Type=Link
URL=trash:/

```
Thats the trash bin, and the part that you can change to hide it is :
```

Hidden=false to Hidden=true 

```
Making it false does the opposite.

---

### Post by maniacmusician on 2006-10-11
but if you have multiple icons and need all of them to dissapear for just a few minutes, you probably dont want to go around doing that. i dunno, i dont think such a program exists. Someone that knows how can probably write a script to change the "Hidden" line in all the desktop icons.

---

### Post by jordanmthomas on 2006-10-11
```
gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "false"
```
will turn them off

If you turn them back on, you may have to click on the desktop and hit F5 to see them

---

### Post by BackInTimeMan on 2006-10-11
Thanks for the replies and sorry for not being very clear.

Yes, what I want to do is to be able to hide or show all desktop items at once, whether they are folders, files or shortcut icons. A script or command that could be put in a launcher and placed on the panel would be ideal.

---

### Post by jordanmthomas on 2006-10-11
Did mine not work?

---

### Post by BackInTimeMan on 2006-10-11
> **jordanmthomas said:**
> Did mine not work?

Thank you, yes, it has worked. I was just trying to get them back again!  :)

I made another launcher and put "true" instead of "false" but they won't come back. I'm working on it...

---

### Post by jordanmthomas on 2006-10-11
Actually, I noticed the same thing about them not coming back just now.
There must be a way to tell nautilus to refresh the desktop.

I'm looking into it as well, because it would be pretty cool to have buttons to turn the icons on/off...I had never thought of it but now I want it to.  :(

(If you log out after setting it to true, they will come back, so don't worry about that)

---

### Post by BackInTimeMan on 2006-10-11
> **jordanmthomas said:**
> Actually, I noticed the same thing about them not coming back just now.
There must be a way to tell nautilus to refresh the desktop.

I'm looking into it as well, because it would be pretty cool to have buttons to turn the icons on/off...I had never thought of it but now I want it to.  :(

(If you log out after setting it to true, they will come back, so don't worry about that)

OK, what it needs to work ATM is to have the Desktop folder (from Places) open (it can be minimised), then the "true" launcher works and the desktop items come back. I don't know why this is so, Nautilus is running all the time isn't it?

---

### Post by jordanmthomas on 2006-10-12
hmmm..it seems nautilus only runs when you actually open a folder or are displaying the desktop.
```
ps -A |grep nautilus
```
Now we're getting somewhere...
```

gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "true" && nautilus -n
```
will get the desktop back, but it takes a long time for me at least, which doesn't really make it a feasible solution.  Still, at least it works.
The -n switch makes it not open your home folder

**edit**  anyone with a better solution, feel free to chime in.

---

### Post by BackInTimeMan on 2006-10-12
That one isn't working for me at all. When you say ".. but it takes a long time...", how long did you mean? I went and made a cofee but still no joy...  ;)

---

### Post by jordanmthomas on 2006-10-12
Well, I meant like 5 seconds.  Not sure why it doesn't work for you though.

---

### Post by BackInTimeMan on 2006-10-12
No, I don't. I have no idea yet about scripting so what does the "&& nautilus -n" do, make Nautilus run without opening a window? Also, I wonder why the command that makes the desktop items dissapear, works without Nautilus running?

---

### Post by jordanmthomas on 2006-10-12
the && xxx means..after the previous command successfully executes, do xxx.
nautilus -n makes nautilus start without bringing up a window

Turning it off works because nautilus is already running if you can see the desktop.  Nautilus is not running after turning the desktop icons off.

---

### Post by BackInTimeMan on 2006-10-12
Right, thanks. Just tried this:

Switch off desktop with the "false" command.
Run "nautilus -n" in the terminal.
Run the (your first) "true" command.
Desktop is still blank.

Run "nautilus -n" in terminal again.
Desktop icons come back.

Weird, so if I run "nautilus -n" before running the "true" command, it doesn't work. Running "nautilus -n" after running the "true" command, does work.

---

### Post by petri on 2006-10-12
This was a neat feature :) I created launchers in panel and hiding icons does work but not showing icons-launcher. In terminal it does work but it would be better in a button.

Is it possible to use the same button?

---

### Post by CatKiller on 2006-10-12
> **petri said:**
> Is it possible to use the same button?

I'd imagine so: write a script that reads that gconf value, and if it's true set it to false, and if it's false, set it to true.

---

### Post by jordanmthomas on 2006-10-12
> **BackInTimeMan said:**
> Right, thanks. Just tried this:

Switch off desktop with the "false" command.
Run "nautilus -n" in the terminal.
Run the (your first) "true" command.
Desktop is still blank.

Run "nautilus -n" in terminal again.
Desktop icons come back.

Weird, so if I run "nautilus -n" before running the "true" command, it doesn't work. Running "nautilus -n" after running the "true" command, does work.

Sorry if I wasn't clear...that *is* how it is supposed to work.

And yes, it should be possible to write a toggle switch...I just don't know enough bash to do it, but it should be really simple as I can see in my mind how it should work.

---

### Post by BackInTimeMan on 2006-10-12
> **jordanmthomas said:**
> Sorry if I wasn't clear...that *is* how it is supposed to work.

You *were* clear enough, I was just wanted it should work the other way round, ie. start Nautilus and then execute the "true" command  ;)

> **jordanmthomas said:**
> And yes, it should be possible to write a toggle switch...I just don't know enough bash to do it, but it should be really simple as I can see in my mind how it should work.

OK, I've managed to make a toggle switch, using your code.

This works properly **only** if there are no Nautilus windows open. If there are any open then the desktop icons will dissapear then reappear again immediately. If you can work out how to make it not do that, I'd be most grateful. At least this has got it working (with the limitation) with one button.

For anyone who wants a step-by-step, here's how:

1. Make a new document on the desktop and call it toggle_icons.bash.

2. Open the document in a text editor and copy and paste this code into it:

```

#!/bin/bash

nautilus -n

gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "false"

gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "true"

```

3. Save and close the file.

4. Right-click on toggle_icons.bash and choose Properties, then click on the Permissions tab and make sure that next to Owner, the Read, Write and Execute boxes are checked.

5. Move toggle_icons.bash to /usr/bin/ like this:

Open a terminal and write or copy and paste the following code pressing Enter after each one. After the second one you'll need to write your password and press Enter again:

```
cd Desktop
```

```
sudo mv toggle_icons.bash /usr/bin/
```

6. Right-click on the panel and select Add to Panel, then click on Custom Application Launcher. Put whatever you want to call your launcher in the Name box and write or copy and paste the following code into the Command box:

```
/usr/bin/toggle_icons.bash
```

Give your launcher an icon if you want, then click OK, and you're done.

That's it. Click on your launcher once to hide the desktop icons and again to show them. Remember the limitation I mentioned at the beginning.

Enjoy!  :D

---

### Post by Dainn on 2006-12-03
Hello :D I just wanted to say thanks for the toggle instuctions.  I was looking around last night and found this.  This works great for me.  I ended up with  my disks showing up on my desktop too, and wanted to "not see them".  After a problem with the install where I ended up looking at a screen with 0 partions available, I was scared to try and attempt to unmount/mount them.  [My heart still races thinking about it :shock: ]

But, as I said earlier, this works great, thanks.

---

### Post by Demon012 on 2006-12-19
Hi guys I was playing with the code you posted and although the code you posted was ok it had not got the conditional statements it needed and it had a problem where nautilus windows would randomly open.

Here is my edited version of your code:

```

#!/bin/bash

desktopVisible=`gconftool-2 --get "/apps/nautilus/preferences/show_desktop"`

if [[ "$desktopVisible" == "true" ]] 
	then echo "Hiding Desktop Icons"; echo `gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "false" && nautilus --no-default-window -n`;
fi

if [[ "$desktopVisible" == "false" ]]
	then echo "Making Desktop Icons Visible"; echo `gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "true" && nautilus --no-default-window -n`;
fi

```

Just paste this into a text editor and save the file as toggleIcons in the /usr/bin folder and then create a shortcut to it on your panel or where ever you like (probably not the best idea to make it a desktop icon though =) ).

Hope this helps,

Demon012

---

### Post by BackInTimeMan on 2006-12-23
> **Dainn said:**
> Hello :D I just wanted to say thanks for the toggle instuctions.  I was looking around last night and found this.  This works great for me.  I ended up with  my disks showing up on my desktop too, and wanted to "not see them".  After a problem with the install where I ended up looking at a screen with 0 partions available, I was scared to try and attempt to unmount/mount them.  [My heart still races thinking about it :shock: ]

But, as I said earlier, this works great, thanks.

You;re welcome. Look at the post by Demon012 in this thread, s/he has fixed the it to overcome the previous limitation. Now it works even if you have a Nautilus window open.

---

### Post by BackInTimeMan on 2006-12-23
> **Demon012 said:**
> Hi guys I was playing with the code you posted and although the code you posted was ok it had not got the conditional statements it needed and it had a problem where nautilus windows would randomly open.

Here is my edited version of your code:

```

#!/bin/bash

desktopVisible=`gconftool-2 --get "/apps/nautilus/preferences/show_desktop"`

if [[ "$desktopVisible" == "true" ]] 
	then echo "Hiding Desktop Icons"; echo `gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "false" && nautilus --no-default-window -n`;
fi

if [[ "$desktopVisible" == "false" ]]
	then echo "Making Desktop Icons Visible"; echo `gconftool-2 --set "/apps/nautilus/preferences/show_desktop" --type boolean "true" && nautilus --no-default-window -n`;
fi

```

Just paste this into a text editor and save the file as toggleIcons in the /usr/bin folder and then create a shortcut to it on your panel or where ever you like (probably not the best idea to make it a desktop icon though =) ).

Hope this helps,

Demon012

This works great and overcomes the limitation I'd mentioned, thanks!  :)

---

### Post by randiroo76073 on 2006-12-23
Thanks for the great script, I'd had a small prgm in 98se that did that, didn't miss it till I saw this post.  Another win for the Ubuntu side :D

---

### Post by Buck2348 on 2006-12-23
Demon012's script works well for me if I DO have a nautilus window open.  If not, toggling the icons back into view produces about 5 instances of a default nautilus window.

Buck

---

### Post by Dainn on 2006-12-23
I just found this again and replaced the old with the new.  Thanks

---

### Post by oenggun on 2006-12-24
hi all,
Sorry for being a bit OOT.

What should I do to make nautilus displaying icons and new icons (eg. when a USB disk is inserted) on the right part of the desktop ?? Like a 'justify right' tools for desktop icons, when I refreshed the desktop. 

How can I toggle desktop icons to the right side of the screen?

For me, right handed user, it's more natural to access icons on the right side of the screen. Probably like the behavior of OSX desktop??

thanks,

---

### Post by BackInTimeMan on 2006-12-24
> **oenggun said:**
> hi all,
Sorry for being a bit OOT.

What should I do to make nautilus displaying icons and new icons (eg. when a USB disk is inserted) on the right part of the desktop ?? Like a 'justify right' tools for desktop icons, when I refreshed the desktop. 

How can I toggle desktop icons to the right side of the screen?

For me, right handed user, it's more natural to access icons on the right side of the screen. Probably like the behavior of OSX desktop??

thanks,

I don' think you can do this at the monment, there is no option in Configuration Editor for it. I did some searching and found a couple of other people wanting to do the same type of thing but not able to achive it. I found a page where this is mentioned as an idea but nothing seems to have been done about it:

[https://wiki.ubuntu.com/Automatic_Desktop_Icon_Organization](https://wiki.ubuntu.com/Automatic_Desktop_Icon_Organization)

I just uncheck "Keep Aligned" and then manually put the icons where I like them.

---

### Post by BackInTimeMan on 2006-12-24
> **Buck2348 said:**
> Demon012's script works well for me if I DO have a nautilus window open.  If not, toggling the icons back into view produces about 5 instances of a default nautilus window.

Buck

I don't know why this is happening but I don't think it's anything to do with the script as it works fine for me with no windows open. Can't think of anything at the moment that might be causing that behaviour... a bug in Nautilus? an odd combination of settings? Have you tried rebooting?  :)

Has anyone else had this happen?

---

### Post by oenggun on 2006-12-24
thanks, BackInTimeMan ..

I wish on the next releases of Gnome would able to do this.

---

