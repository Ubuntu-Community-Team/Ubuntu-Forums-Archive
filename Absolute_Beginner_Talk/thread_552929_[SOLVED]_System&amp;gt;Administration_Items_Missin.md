---
title: "[SOLVED] System&amp;gt;Administration Items Missing!?!?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by MilitaryPawn on 2007-09-17
I'm a total noob to Ubuntu, and I just messed something up! :/  Under the System>Administration menu I lost like half of the items listed.  The only ones I have now are BootUp-Manager, Keyring Manager, Network Tools, Printing, System Log, System Monitor, and Update Manager.  I have no idea what I did to make the other ones disappear and I have no idea how to get them back.  Any help would greatly be appreciated!  Oh and I'm running Fiesty Fawn if that matters.  Thanks in advance! :confused:

---

### Post by julian67 on 2007-09-17
Sounds to me like you uninstalled gnome-system-tools. Easily fixed as long as you are online:

```
sudo apt-get install gnome-system-tools
```

or you can use Synaptic to re-install the package.

edit: possibly you don't even need to be online, this will be on the install CD and maybe also cached on your hard disk.

---

### Post by MilitaryPawn on 2007-09-17
I also just realized that the option for Add/Remove Programs is gone.  I looking around as some more threads and got closer .. . i think  If I just right click on system there is an option that says Edit Menus.  When I go there and scroll down to the Administration folder all of the things that I am missing are listed there but they do not have the check boxes filled in and when I try to select them they just uncheck themselves 1 second later.  It won't allow me to select Add/Remove programs either.  So everything is still installed or at least it looks like it but I just cant access it.  Maybe I have to login as root and change settings around??  If so I have no idea how to do that either :/.

---

### Post by julian67 on 2007-09-17
> **MilitaryPawn said:**
> I'm a total noob to Ubuntu, and I just messed something up!

Ok it's time to say what it is you were doing just before it got messed up :-)

---

### Post by Majorix on 2007-09-17
Try to restore your icons with alacarte:
```
sudo alacarte
```

---

### Post by shooters on 2007-09-17
If you are not logged as an administrator, those items will not appear in the menu (because you need root privileges and not admin account can't run sudo)

---

### Post by Majorix on 2007-09-17
> **shooters said:**
> If you are not logged as an administrator, those items will not appear in the menu (because you need root privileges and not admin account can't run sudo)

Sorry but I believe you could be wrong. They WILL show up, and will ask for the root pass. So if you don't know the root pass you still can't run them.

---

### Post by shooters on 2007-09-17
I'm running on Gutsy and exactly the menu items mentioned above appears when I log on using a non-root account.  So this is probably the cause of the problem.

---

### Post by macogw on 2007-09-17
> **Majorix said:**
> Sorry but I believe you could be wrong. They WILL show up, and will ask for the root pass. So if you don't know the root pass you still can't run them.

No they don't.  If your account is a "desktop user" account, those items are missing completely.  If it is "administrative user" they are there and use gksudo.  Other distros (like Debian) keep them in the menu and ask for a root password.  Ubuntu doesn't do that because Ubuntu doesn't have a root password.

---

### Post by julian67 on 2007-09-17
The OP is running Feisty not Gutsy. In Feisty all those menu items should be visible in a regular account and it should be possible to toggle the visibility on/off in the menu editor.

---

### Post by macogw on 2007-09-17
> **shooters said:**
> I'm running on Gutsy and exactly the menu items mentioned above appears when I log on using a non-root account.  So this is probably the cause of the problem.

You are always non-root in Ubuntu.  That's what happens when you run using a non-administrative-access account.  Yeah, there is a difference.  Root has full-time access to admin functions.  Admins have to enter their password and go all "Simon Says."

---

### Post by macogw on 2007-09-17
> **julian67 said:**
> The OP is running Feisty not Gutsy. In Feisty all those menu items should be visible in a regular account and it should be possible to toggle the visibility on/off in the menu editor.

No, in Feisty most Admin items are missing when using a "desktop" account as opposed to "administrative account."  I haven't even tried Gutsy.  Feisty hides a lot of stuff from desktop users in the admin menu.

---

### Post by lisati on 2007-09-17
> **macogw said:**
> No, in Feisty most Admin items are missing when using a "desktop" account as opposed to "administrative account."  I haven't even tried Gutsy.  Feisty hides a lot of stuff from desktop users in the admin menu.

ditto with the copy of Feisty I use - some things are hidden depending on what sort of account you log in with.

---

### Post by julian67 on 2007-09-17
shall we assume the *new user* is using the *defaults* and not worry about it? ;-)

---

### Post by MilitaryPawn on 2007-09-17
I think the last thing I did was change a setting under User and Groops for my account.  I was trying to give my self administrative privlages and I was just messing with things.  But I'm pretty sure that was the last thing I did, I think it was like a check box in User and Groops but now I can't get back there to change it back.  Is there a way to access User and Groop settings through the terminal or anything like that?  I might be able to undo what I did last.  Not sure if that would even fix it but if there is a way to get there without having the icon to click on that would be useful information! :)

Oh yeah and I think I mentioned it before also that I can no longer see the Add/Remove Programs icon under Applications.

---

### Post by MilitaryPawn on 2007-09-17
I was able to get to the menu editor and all of the programs are there but they are unchecked and when I try to check them they just uncheck.  Maybe if I can login as root or whatever then I can edit the settings back that I think I changed last.  But how do I login as root it wouldnt let me from the main login page???

---

### Post by julian67 on 2007-09-18
go into users and groups and make sure you are a member of the following groups:
[LIST]
[*]Administer the system
[*]Connect to Internet using a modem
[*]Use audio devices
[*]Use floppy drives
[*]Use modems
[*]Scanners[/LIST]

and you should be back to default settings

If you need to do this vial cli use the command usermod. Maybe you need to reboot into single user mode to do this.

---

### Post by MilitaryPawn on 2007-09-18
I typed in usermod and it came up with a list of things but I have no idea how to use any of them.  I'm really Ubuntu Illiterate!!!  Is there any way to launch the Users and Groups GUI based menu through the terminal?

---

### Post by Lord Illidan on 2007-09-18
Try this.

Reboot.

From the menu, chose Failsafe.

You should find yourself at a prompt.

From there type :

```
usermod -a -G  admin  <your username>
```For example, I type ```
usermod -a  -G admin jean
```

---

### Post by MilitaryPawn on 2007-09-18
usermod -a admin -G chris worked!!!  Lord Illidan you are amazing!  IDK how you know what your are doing but you do know what you are doing!  Thank you so much!

I'm not sure, maybe I just did something wrong the first time, because when I typed it in it didnt say anything after I typed that in and I had no idea how to get out and boot into Ubuntu normally so I just turned it off and when it came on I still had the same problem so I went back into restore mode or failsafe or w/e and typed it in again, it still didn't say anything but just to be safe I typed in usermod -a -G admin chris because it looked like that was the way it should be typed in from the menu describing the commands.  IDK if the way I typed it in first was right or the way I typed it in second was right but I just turned it off and back on and everything was back to normal!  I appreciate it so much!  Thanks a ton!=D> :) :-D :D :guitar:

Thanks!

Chris

If anyone else has this same problem just follow what Lord Illidan said and maybe just to be safe type it in both ways lol idk.  Worked for me!

---

### Post by Lord Illidan on 2007-09-19
I'm sorry, I should have given you this command : ```
usermod -a -G admin chris
```I will edit my previous post.

To turn off the pc from the console, just type : halt or sudo halt. (halt if you're root, and sudo halt if you are a normal user). To reboot : type, reboot :P

How did I know the command? By typing man usermod . The man pages can be accessed by typing man <any command>.

So, man ls will reveal the man page for ls. This way you can get a good deal out of your OS without having to resort to the forums...handy if your internet connection is down.

EDIT : You can now mark this as solved.

---

### Post by MilitaryPawn on 2007-09-19
Its all good.  Oh cool I have never heard of that command before.  Just tried it and that will be very helpful in the future I'm sure!  Thanks again!

---

### Post by Tony_photoplus on 2008-02-19
I am having the same problem, but I can't seem to boot into 'Failsafe' mode.  Any help you can suggest?  If I can get there I can move onto more questions, like how do I get rid of this admin and password loggins.  I just want to turn my comp an and it load up without having to come back and see I haven't logged in and then wait for it to load.  As I am the only user I don't need this.   I think I did the same mistake trying to get rid of this admin logging in and having to type password evrytime I wanted to change anything or look into files etc.  This Ubuntu is completely new to me.  I have thrown out the windows knowledge I have and am completely lost at sea.

Tony_photoplus

---

### Post by Tony_photoplus on 2008-02-19
Morphine hasn't completely killed my brain cells!  I realised there is a very short flash of something 'esc or 1'.  So I managed to get there and resolve my problem.  Thanks for the info before.

Tony-photoplus

---

