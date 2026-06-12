---
title: "A few questions regarding Ubuntu"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Stall on 2007-09-22
Good day everyone. I recently began to use Ubuntu, and really enjoy it. However, I have a few questions regarding it, and was hoping I could get some answers.

1) Is there anything similar to the 'program files' on Windows in Ubuntu?
2) What is a good image viewing/resizing/cropping program similar to Irfan View? I really am dependant on this program, and would love to have a version on the Linux.
3) How do I install new themes onto Ubuntu (GTK)? And how do I change the symbol in the upper left hand corner? I really like customization, and Ububtu seems to be quiet strong in that category, so I would love to take advantage of this.
4) On the GTK, can I use bother GTK 1.0 and 2.0, or does Ubuntu 7.0.4 just use one of the two?
5) Are there any tutorials on mastering the Terminal? 
6) I will be duel booting Ubuntu with Vista. each on their own HDD. Will this be any trouble?
7) Is there any way to get certain pieces of hardware to be picked up by Ununtu? Namely a Creative Zen Microphoto?

I thank everyone for their time and help.
Stall

---

### Post by Dr Small on 2007-09-22
1.) Your Applications menu at the top is similar to "Program Files".
2.) I honestly do not know what Irfan is, but you can use The Gimp for viewing, resizing and cropping.
3.) I do not know how you would change the ubuntu symbol on the menu, although there is probably some way to do this. You can get different themes from [Gnome-look.org](http://gnome-look.org)
4.) I have no idea...
5.) [This url](http://www.linuxcommand.org/) explains alot.
6.) I think you will need to configure GRUB properly to get it to work out, but it can be done.
7.) Your microphone should be auto-detected, if I am not mistaken.

Dr Small

---

### Post by Steveway on 2007-09-22
4.) Easy, GTK 1.0 themes are for apps that use GTK 1.0 and vice versa.
Just use GTK 2.0 themes, you won't really come across GTK 1.0 apps.

---

### Post by slira on 2007-09-22
Hi there,
Welcome to ubuntu. Hope you have fun.
As for your questions:
1)Well, your programs are installed in many different places (different parts of the program belong in different zones). In practice, all you'll need for now is /usr/bin (where the executables (not .exe's, they are the "starters" for the programs) However, most things you need can be done either from the apps menu or from the shell, no need to go  there and start them manually.

2)personally, I use gThumb. It has all the nifty tools needed for the everyday work and isn't excessively heavy on the system.

3)Not really sure. For KDE, you can download them from the web and open them with the display configurer (kmenu->system settings->display). I think there's something similar to GTK but not sure:(

4)NO IDEA!!! I'd use the most recent one but whatever, Just try it out.

5)If you mean learning the terminal commands,
[FONT="Courier New"]help[/FONT]
in the shell will give you an idea. Also,
[FONT="Courier New"]"command you want" --help[/FONT]
or
[FONT="Courier New"]man "command you want"[/FONT]
(without the quotes obviously) will print out a more detailed explanation. Use q to exit the man. If you need more info, we can always look at the ubuntu wiki: ([https://help.ubuntu.com/community/CommandlineHowto]("https://help.ubuntu.com/community/CommandlineHowto"))

6)Most likely not, but Vista is quite the unpredictable fella so take care. Since they're each in their own HDD, on startup you can press F11 (or whatever it is for you) and select the disk you want to boot from. Selecting Ubuntu's will take you to the GRUB boot loader screen. Selecting Vista's will take you directly to that awesome, bug free, amazingly smooth and easy OS [/sarcasm]

Once again, have fun using ubuntu and welcome to the community.

slira

---

### Post by Orbital75 on 2007-09-22
> **Stall said:**
> Good day everyone. I recently began to use Ubuntu, and really enjoy it. However, I have a few questions regarding it, and was hoping I could get some answers.

1) Is there anything similar to the 'program files' on Windows in Ubuntu?
2) What is a good image viewing/resizing/cropping program similar to Irfan View? I really am dependant on this program, and would love to have a version on the Linux.
3) How do I install new themes onto Ubuntu (GTK)? And how do I change the symbol in the upper left hand corner? I really like customization, and Ububtu seems to be quiet strong in that category, so I would love to take advantage of this.
4) On the GTK, can I use bother GTK 1.0 and 2.0, or does Ubuntu 7.0.4 just use one of the two?
5) Are there any tutorials on mastering the Terminal? 
6) I will be duel booting Ubuntu with Vista. each on their own HDD. Will this be any trouble?
7) Is there any way to get certain pieces of hardware to be picked up by Ununtu? Namely a Creative Zen Microphoto?

I thank everyone for their time and help.
Stall

I'd give GQview a look, it's a very nice Image Viewer.
Gimp is a very nice Photo Shop Clone and will give you
very advanced photo editing. 

As far as adding new themes and GTk's, this is very easy.
Take a look at  [http://www.gnome-look.org](http://www.gnome-look.org) . this is a very cool site full of nice theme.
All you will need to do is download a theme then go to system ----- preferences --- themes.
now just select install, select your theme and it will do it all for you. :-)
Can't beat that !!!

---

### Post by Stall on 2007-09-22
Thanks for your replies. I really appreciate your time.
[quote=Orbital75]All you will need to do is download a theme then go to system ----- preferences --- themes.
now just select install, select your theme and it will do it all for you. [/quote]
Is there any need to extract them? 

[quote=slira]6)Most likely not, but Vista is quite the unpredictable fella so take care. Since they're each in their own HDD, on startup you can press F11 (or whatever it is for you) and select the disk you want to boot from. Selecting Ubuntu's will take you to the GRUB boot loader screen. Selecting Vista's will take you directly to that awesome, bug free, amazingly smooth and easy OS [/sarcasm][/quote]
Unfortunately, I have too much of a need for Windows to completely switch over. So I figured I would simply use an old HDD for Linux. Get aquinted with the OS, and someday hopefully completely switch over.

[quote=Dr Small] I think you will need to configure GRUB properly to get it to work out, but it can be done.[/quote]
Might there be a tutorial online somewhere on how to do this properly? 

I also appreicate all the suggetions on image viewing/resizing programs. Thank you agian.

---

### Post by iansane on 2007-09-22
Applications menu is similar to "start menu" not program files. Program files are scattered everywhere. All the executables are not necessarily in "bin" all mine aren't anyway. I don't know where they all are though. What I do know is that some important stuff is in "home/yourusername" These are similar to the hidden "application data" folder in that this is where you can find your "mail" folder for thunderbird, for example.

---

### Post by Tyke91 on 2007-09-22
here's a really good site for mastering shell commands
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

different themes can change your little top left icon (i use the ubuntu-studio theme for mine because i really like the blue thing)

---

### Post by perce on 2007-09-22
You don't really need to know where program files are: when you install a program the installer takes care to put it in the right place, and when you start a program, either from the menu or from the terminal, all what you need to know is he name of the program, not where its files actually are. 

If yours is just a curiosity, most program files are in one of these four directories: /bin (essential programs for the OS),  /sbin (essential administration programs), /usr/bin (most programs for normal users) and /usr/sbin (non essential administration programs). Configuration files for a program are either in your home directory, usually as hidden files or directory (just add . in front of a file or directory name to hide it) or in /etc.

---

### Post by iansane on 2007-09-23
I'm curious too.
If you told me I didn't need to know where program files are in Windows I would say you were insane but maybe that's cause I couldn't always rely on programs to install corectly or uninstall mostly. Maybe curiosity and overthinking things combined are what is making Ubuntu hard to understand for me. It's probably a good idea to have faith in the Ubuntu and get used to it before I go digging to deep. 

Hard to do when the voices in my head want to know.

---

### Post by R.Bucky on 2007-09-24
It is no problem to use Irfanview in linux. you will need to install wine (Windows Emulator).```
sudo apt-get install wine
```
Then, simply click on the irfanview.exe or right-click and select open-with Wine...
I use the program almost daily without a hitch. 
Once wine is installed, take a look at the install directory to get an idea of any shortcuts that you might want to add. the directory is 
/home/your user-name/.wine

---

