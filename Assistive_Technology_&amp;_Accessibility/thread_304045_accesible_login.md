---
title: "accesible login"
date: 2006-11-21
forum: Assistive Technology &amp; Accessibility
---

### Post by sir_skiner on 2006-11-21
Hi,
first of all I'd like to thank you for uour job on the accessibility in ubuntu, especially for onboard, which makes my life with ubuntu much easier. last time gok was usable for me was on slackware 9.0.

my question is: how can accessible login be done? I mean, now when I want to log in I have to ask some one to enter login and pass for me or to set up GDM to loging me in automatically. can it be done so I could enter them through onboard or any other osk?

---

### Post by frafu on 2006-11-21
Hello, 

Making onboard available at the login screen is one of the next targets for onboard. [See here]("http://ubuntuforums.org/showpost.php?p=1568608&postcount=2"). 

In the meantime, you might set it up by yourself by following the indications of the last messages of [this thread]("http://ubuntuforums.org/showthread.php?t=267051"). 

frafu

---

### Post by sir_skiner on 2006-11-21
thank you for your answer, but onnboard doesn't start with gdm. do I have to ad this line at the  very end of gdm's config file or at the end of the loop?

---

### Post by frafu on 2006-11-21
I have not tried it myself, as I have automatical login enabled; however as I understand you should make the following:
(do it at your own risk; please don't do it if you have data on your computer that you don't want to lose.) 

Open terminal and type:
```
  
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.backup
gksudo gedit /etc/gdm/Init/Default

``` 

You will be asked for your password. 
The first line makes a backup of the file we are going to edit. The second line will open the shell script named 'Default' located in /etc/gdm/Init in the Text Editor named gedit. You have to edit that file. 

You will have to add the 2 words 'exec onboard' before the last line. The bottom of the file should look like: 
```
  
fi

exec onboard &

exit 0

``` 

Save the file and close gedit. 




Afterwards, open the menu: 
System->Administration->Login Window

The window containing the preferences of the Login Window will open. In this window do the following: 

- choose the tab named 'Local'
- click on the popup at the right of 'Style' and set it to 'Plain'. (mine was set to 'Themed') 
- close the window 



If I understood the indications in the other thread correctly, now you should see onboard at the login screen. 


frafu

---

### Post by sir_skiner on 2006-11-22
ah, a little corection. there should be:
```
exec onboard&
```
including pure 'exec onboard' makes gdm startup hangs before all is done. everything else cheks.

last thing. onboard starts fine, but it starts in the center of screen so it overcasts gdm login window. how to change its startup position ang geometry through the command line?

---

### Post by frafu on 2006-11-22
Thanks for the indication to add an & to the onboard starting command; I have fixed it. 

I have further replaced sudo with its version for graphical applications gksudo.


Unfortunately, I don't know if it is possible to tell onboard its starting position. I will ask the developer... 

frafu

---

### Post by t0rtois3 on 2006-11-22
OK this seems to work, it's a quick hack using some code I left in  to do something else then forgot about.

Add this after line 100 in /usr/share/onboard/sok.py

self.window.do_set_gravity(gtk.gdk.GRAVITY_SOUTH_EAST)

note due to a bug it does not matter whether you change SOUTH_EAST to NORTH_EAST etc. onboard will appear in the top left.

---

### Post by ka9qlq on 2007-04-04
Wow this is cool! xvkb allowed me access to Linux, onbord will allow me security. Hay can you make the letters the same size as the keys like xvkbd? How customizable is the interface? Is it still in development? who could I offer suggestions to?

---

### Post by frafu on 2007-04-05
> **ka9qlq said:**
> Wow this is cool! xvkb allowed me access to Linux, onbord will allow me security. Hay can you make the letters the same size as the keys like xvkbd? How customizable is the interface? Is it still in development? who could I offer suggestions to?

Glad to see you are satisfied. 

You can find a reply to your layout question in [your other thread]("http://ubuntuforums.org/showthread.php?t=400661"). 

Yes, it is still in development; have a look at these pages: 
[https://wiki.ubuntu.com/Accessibility/Specs/SOK?highlight=%28sok%29](https://wiki.ubuntu.com/Accessibility/Specs/SOK?highlight=%28sok%29)
[https://wiki.ubuntu.com/Accessibility/Projects/onBoard?highlight=%28onboard%29](https://wiki.ubuntu.com/Accessibility/Projects/onBoard?highlight=%28onboard%29)
[https://launchpad.net/onboard](https://launchpad.net/onboard)

Have a nice day.

---

### Post by v.cecchetto on 2007-07-03
I played a little to give the correct size to the onboard login keyboard, on my laptop (1280x800).

Edit /usr/share/onboard/KbdWindow.py

raw 21-25

...................................................
#if x and y:
#	self.set_default_size(x,y)
#else:
self.set_default_size(600,180)
#self.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
...................................................

Play with the number 600, 180, change them till you get the desired size for your keyboard. 

Aware: the language is tab sensitive, so u have to remove the initial tab in the line 
self.set_default_size(600,180)
to allineate with the surrounding code or it doesn't function and the login keyboard disappear.

:p

---

### Post by frafu on 2007-07-04
@ v.cecchetto

Am I missing something? 

You can grab the lower right corner with your mouse and resize the keyboard.. 

Moreover, the keyboard starts with the size it had when it was quitted. 

Francesco

---

### Post by v.cecchetto on 2007-07-04
I use Feisty and at the login prompt i find a keyboard on my screen that is not resizable.

More exactly to activate the login-keyboard i followed this procedure:

System > Preferences > Accessibility > Assistive Technology Preferences 

Check:
- Enable assistive technology
- Password dialogues as floating windows
- Start on-screen keyboard at login

sudo gedit /etc/gdm/Init/Default

insert before the last line the following

exec onboard &

At this point i see nothing again at the login prompt i need the following steps

System > Administration > Login Window > (Tab) Local > Style: Plain

Ok, now i see the keyboard at the login but it's too big and overlap the prompt, and also i cannot resize it.

So i found that trick to make it smart for my resolution 1280x800.

:popcorn:

---

### Post by frafu on 2007-07-10
@v.cecchetto

Thanks for your explanation; it already helped a person in [this post]("http://ubuntuforums.org/showpost.php?p=2997924&postcount=54"). 

Maybe that you are also able to tell him how to move onboard to a different location on the login screen. 

Anyway, thanks in advance. 

Francesco

---

### Post by v.cecchetto on 2007-07-11
> **frafu said:**
> @v.cecchetto

Thanks for your explanation; it already helped a person in [this post]("http://ubuntuforums.org/showpost.php?p=2997924&postcount=54"). 

Maybe that you are also able to tell him how to move onboard to a different location on the login screen. 

Anyway, thanks in advance. 

Francesco

Done. 

Thank's you for the advice. :)

---

### Post by frafu on 2007-07-11
@v.cecchetto

Thanks to you for your help.

---

### Post by phenest on 2007-09-30
Although my stylus works perfectly in Ubuntu 7.04, I am unable to use it at login for the on-screen keyboard.

Any ideas?

---

### Post by frafu on 2007-09-30
@phenest

What onscreen keyboard are you talking about: onboard or gok? 

Francesco

---

### Post by phenest on 2007-09-30
I'm using OnBoard. I haven't tried GOK. This might be more a Wacom issue. The stylus works but erratically as the mouse cursor seems to want to be in the lower-right corner constantly.

---

### Post by frafu on 2007-09-30
If there isn't one already, I would advise you to file a bug against onboard on [launchpad]("https://bugs.launchpad.net/"). 
(I am assuming that you mean the lower right corner of onboard.)

---

### Post by t0rtois3 on 2007-10-01
Does this only happen when running onBoard

---

### Post by phenest on 2007-10-02
It only happens at the login screen, regardless of whether OnBoard is running or not. I can use a mouse ok, but if I use the stylus, the cursor keeps jumping to the lower-right of the screen.

---

### Post by t0rtois3 on 2007-10-03
OK, please file a bug report on launchpad.net against GDM.

---

### Post by phenest on 2007-10-05
> **t0rtois3 said:**
> OK, please file a bug report on launchpad.net against GDM.


I found the reason and the solution: simply uncheck 'Enable accessible login' in System>Administration>Login Window - Accessibility tab.

---

### Post by frafu on 2007-10-05
If the issue has not already been filed by somebody, I think that you should nevertheless file a bug against gdm on [launchpad]("https://bugs.launchpad.net/gdm/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=gdm") and also in GNOME's [bugzilla]("http://bugzilla.gnome.org/").

---

