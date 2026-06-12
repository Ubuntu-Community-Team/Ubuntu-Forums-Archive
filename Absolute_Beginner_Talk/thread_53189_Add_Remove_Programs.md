---
title: "Add /Remove Programs"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-30
I click on Applications / System Tools / Add /Remove Programs but it doesn't open? my cursor is whirring away as if the application is about to open but it keeps on whirring for infinity until i click 'close'

Could someone tell me what the reason for this might be?

thank you

sophtpaw

---

### Post by heimo on 2005-07-30
What happens if you open a terminal and type this?
 ```
sudo python /usr/bin/gnome-app-install
```

---

### Post by Omnios on 2005-07-30
I have the same problem those are the core stuff like browser etc. I just click advanced to get the rest of synaptic working. You can get the browser working there to.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]What happens if you open a terminal and type this?
 ```
sudo python /usr/bin/gnome-app-install
```[/QUOTE]

Thank you for the support. This is the transcript:


sudo python /usr/bin/gnome-app-install
Password:
Reading package lists... Done
Building dependency tree... Done
Traceback (most recent call last):
  File "/usr/lib/gnome-app-install/AppInstall.py", line 125, in idle
    self.updateCache()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 144, in updateCache
    self.populate_menu()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 242, in populate_menu
    import locale ; menu.setLocale(locale.getlocale(locale.LC_MESSAGES)[0])
AttributeError: Menu instance has no attribute 'setLocale'

And the cursor is stuck there, flashing, and it won't go back to a new command line (i don't know what to call it. Like when one opens a terminal afresh, or after a successful execution of a command) Actually, it has eventually come back to home$ blahblah:

Also Add/Remove Programs opened like it would if i had gone straight to Applications/ System Tools, but of course doesn't open

Please tell me more

sophtpaw

---

### Post by heimo on 2005-07-30
Well... Something's broken. Sorry, I have no idea. But could you use Synaptic to install what ever you were looking for? System->Administration->Synaptic Package Manager

You should probably check that your systems is fully up to date. You can do this in synaptic or on command line (terminal) like this:
 ```
sudo apt-get update
sudo apt-get upgrade

```

Then you could try the Add/Remove programs again. I tried to find other threads with same problem, but didn't find any, and I haven't seen same problem earlier.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=Omnios]I have the same problem those are the core stuff like browser etc. I just click advanced to get the rest of synaptic working. You can get the browser working there to.[/QUOTE]

I'm sorry Omnios. I don't understand, " i just click advanced to get teh rest of synaptic working. You can get the browser working there to" ??

Can you explain what you mean, and whether you are saying that you have found a way to rectify the problem or another way to get to the application Add/Remove Programs ?

regards,

sophtpaw

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]Well... Something's broken. Sorry, I have no idea. But could you use Synaptic to install what ever you were looking for? System->Administration->Synaptic Package Manager

You should probably check that your systems is fully up to date. You can do this in synaptic or on command line (terminal) like this:
 ```
sudo apt-get update
sudo apt-get upgrade

```

Then you could try the Add/Remove programs again. I tried to find other threads with same problem, but didn't find any, and I haven't seen same problem earlier.[/QUOTE]

Shame. thank you for trying. I am fully updated and upgraded, as it happens. I wasn't actually trying to add/remove anything, and if i did i'm sure Synaptic could do the job. But it's just nice to know it works (that everything works on the Desktop) and to have a look at how it looks. I was in fact following [https://wiki.ubuntu.com/UbuntuHowCome](https://wiki.ubuntu.com/UbuntuHowCome) and he was talking one through Add/Remove Programs, which prompted me to notice that it wasn't working. Actually i noticed yesterday already, but felt prompted now to ask whether anyone knew how to fix it.

Thanks again,

sophtpaw

---

### Post by heimo on 2005-07-30
Can you post output of command locale? Specificly, the value of LC_MESSAGES, mine says: LC_MESSAGES="en_US.UTF-8"

I don't know if this leads anywhere, but I think this is related to your problem (maybe). I don't have much time to dive into this problem, but maybe someone will. 

Zzzz...


EDIT: Oh, and md5sum /usr/lib/gnome-app-install/AppInstall.py - do we have the same version? Mine says 5aae4bed1ba467bd5bdd9d3bcc801b2a

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]Can you post output of command locale? Specificly, the value of LC_MESSAGES, mine says: LC_MESSAGES="en_US.UTF-8"

I don't know if this leads anywhere, but I think this is related to your problem (maybe). I don't have much time to dive into this problem, but maybe someone will. 

Zzzz...


EDIT: Oh, and md5sum /usr/lib/gnome-app-install/AppInstall.py - do we have the same version? Mine says 5aae4bed1ba467bd5bdd9d3bcc801b2a[/QUOTE]

I don't know how to post output of command locale. that is like a language from another planet. If you want to give me step by step instructions and walk me through it great, but i hear that you don't have much time to dive into this problem too. So... :roll:

---

### Post by heimo on 2005-07-30
Open Applications->System Tools->Terminal

type: locale    (enter)

You'll see a list like this:
 ```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
``` 

I'm interested in the LC_MESSAGES value. I try to help you fix this, but I'm not sure if I can. I'm also running different version of Ubuntu (Breezy Badger), so my setup may differ.

Now type:
md5sum /usr/lib/gnome-app-install/AppInstall.py
and post the outputted line.

Thanks!

:) It's getting late on this side of planet. I have to get some sleep, but I'm going to get back to this tomorrow.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]Open Applications->System Tools->Terminal

type: locale    (enter)

You'll see a list like this:
 ```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
``` 

I'm interested in the LC_MESSAGES value. I try to help you fix this, but I'm not sure if I can. I'm also running different version of Ubuntu (Breezy Badger), so my setup may differ.

Now type:
md5sum /usr/lib/gnome-app-install/AppInstall.py
and post the outputted line.

Thanks!

:) It's getting late on this side of planet. I have to get some sleep, but I'm going to get back to this tomorrow.[/QUOTE]


Common Finland - not so late

 O:) 

conrad@x1-6-00-0b-6a-16-78-f0conrad:~$ md5sum /usr/lib/gnome-app-install/Appinstall.py
/usr/lib/gnome-app-install/Appinstall.py: No such file or directory
conrad@x1-6-00-0b-6a-16-78-f0conrad:~$


i don't know if you wanted the first part of the transcript, i.e out put for locale?

---

### Post by heimo on 2005-07-30
Hmm... Try:
 ```
sudo apt-get install gnome-app-install

``` 
Does it say it's already latest version?

Now I'm confused. How about:
 ```

ls -l /usr/lib/gnome-app-install/

``` 
and...
 ```

sudo apt-get install python-xdg

``` 

Do you have ubuntu-desktop properly installed:

 ```
sudo apt-get install ubuntu-desktop

``` 

And yes, post the output of that locale command, too. :)

Yeah, not late enough. ;D

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]Hmm... Try:
 ```
sudo apt-get install gnome-app-install

``` 
Does it say it's already latest version?

Now I'm confused. How about:
 ```

ls -l /usr/lib/gnome-app-install/

``` 
and...
 ```

sudo apt-get install python-xdg

``` 

Do you have ubuntu-desktop properly installed:

 ```
sudo apt-get install ubuntu-desktop

``` 

And yes, post the output of that locale command, too. :)

Yeah, not late enough. ;D[/QUOTE]

hehe...the night is young. In Finland you have 24hrs of light in Summer? like in iceland? 

anyway, locale=
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

and to the other question; yes, everything is the latest update and upgrade(version):

conrad@x1-6-00-0b-6a-16-78-f0conrad:~$ ls -l /usr/lib/gnome-app-install/
total 36
-rw-r--r--  1 root root 17052 2005-04-06 10:08 AppInstall.py
-rw-r--r--  1 root root 14359 2005-07-29 18:13 AppInstall.pyc
conrad@x1-6-00-0b-6a-16-78-f0conrad:~$ sudo apt-get install python-xdg
Reading package lists... Done
Building dependency tree... Done
python-xdg is already the newest version.

except for sudo apt-get install ubuntu-desktop

...The following extra packages will be installed:
  firefox-gnome-support mozilla-firefox-gnome-support
The following NEW packages will be installed:
  firefox-gnome-support mozilla-firefox-gnome-support ubuntu-desktop
....

which i have successfully done! or the computer did it  :-? 

--
sophtpaw

---

### Post by heimo on 2005-07-30
Oh! Now I see why it wasn't found earlier... it's not:
md5sum /usr/lib/gnome-app-install/Appinstall.py

It's
md5sum /usr/lib/gnome-app-install/AppInstall.py

:) i vs. I quite a small change... Well. Anyway, I'm back to square one. I'm unable to reproduce the error, and thus it's quite hard to debug. It's probably not even on that file, but run that md5sum anyway, so we can see if that file is same on our systems.

---

### Post by UbuWu on 2005-07-30
[QUOTE=sophtpaw]I click on Applications / System Tools / Add /Remove Programs but it doesn't open? my cursor is whirring away as if the application is about to open but it keeps on whirring for infinity until i click 'close'
[/QUOTE]

Happens with me as well... you are not the only one. Didn't make time yet to find out why.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]Oh! Now I see why it wasn't found earlier... it's not:
md5sum /usr/lib/gnome-app-install/Appinstall.py

It's
md5sum /usr/lib/gnome-app-install/AppInstall.py

:) i vs. I quite a small change... Well. Anyway, I'm back to square one. I'm unable to reproduce the error, and thus it's quite hard to debug. It's probably not even on that file, but run that md5sum anyway, so we can see if that file is same on our systems.[/QUOTE]

 conrad@x1-6-00-0b-6a-16-78-f0conrad:~$ md5sum /usr/lib/gnome-app-install/Appinstall.py
/usr/lib/gnome-app-install/Appinstall.py: No such file or directory
 ](*,) 
heimo, i do not see the difference between the one line md5sum....and the other md5sum...line anyway, i ran it and got no such file or directory as you can see above. 
I know that the first time i installed Ubuntu Add/Remove/programs worked. Because there was a fish i put on the panel from there. Anyhow i reinstalled Ubuntu took care of repositories and everything and this is just strange. I hear that other people are experiencing this too - sounds like a ubuntu bug/tendency

--
sophtpaw

---

### Post by heimo on 2005-07-30
No no... you didn't run the second one, you ran the first one. :D There's a lowercase i in the one you ran, and uppercase I in the second one. Unix / Linux filesystems are case sensitive. That's why it didn't find the file. But this won't solve the problem, it will only tell me if I have a same version of that file. I don't know if I can track the problem, but if not, maybe we can at least file a good bug report.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]No no... you didn't run the second one, you ran the first one. :D There's a lowercase i in the one you ran, and uppercase I in the second one. Unix / Linux filesystems are case sensitive. That's why it didn't find the file. But this won't solve the problem, it will only tell me if I have a same version of that file. I don't know if I can track the problem, but if not, maybe we can at least file a good bug report.[/QUOTE]


I'm sorry Heimo, maybe it is getting late  :???:   but i did not see any difference of any 'i' or otherwise in either line, as i said. 

Tell me exactly what to insert, because i do not know which i should be capitalised

help me so i can help you help me,

---

sophtpaw

---

### Post by heimo on 2005-07-30
```
md5sum /usr/lib/gnome-app-install/Appinstall.py
md5sum /usr/lib/gnome-app-install/App**I**nstall.py
-------------------------------------^---------

```


EDIT: And time to learn some X tricks. Highlight the text, move mouse cursor over terminal window (left click to focus if neccessary) and click with middle mouse button (or wheel). Just highlighting ("painting") the text copies it to clipboard, middle mouse button pastes it. Very convenient.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]```
md5sum /usr/lib/gnome-app-install/Appinstall.py
md5sum /usr/lib/gnome-app-install/App**I**nstall.py
-------------------------------------^---------

```


EDIT: And time to learn some X tricks. Highlight the text, move mouse cursor over terminal window (left click to focus if neccessary) and click with middle mouse button (or wheel). Just highlighting ("painting") the text copies it to clipboard, middle mouse button pastes it. Very convenient.[/QUOTE]


Now we're talking  :grin: 


thats what came back from:
 md5sum /usr/lib/gnome-app-install/AppInstall.py


44fdf028934dd4018d85c2dd0242c798  /usr/lib/gnome-app-install/AppInstall.py

Now you will see if it matches your own code? any maybe make a good report. As long as it helps and we're moving in the right direction,

share the care,

sophtpaw

---

### Post by heimo on 2005-07-30
I don't know if it was really worth the trouble. ;D But at least I'll be able to find the same version of the file (tomorrow) and see if the problem is in it. I doubt, but you have to start somewhere. Thank you very much, I'll post you what I find.

Probably would be good idea to search other similar threads on this forum, if it's common problem, this may have been solved dozen times already.

Good night!

---

### Post by Ubunted on 2005-07-30
I had this problem myself. Here's the fix: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

Download and extract "the patched and compiled version of gnome-app-install to solve the smeg-problem"

Then open a terminal in the extracted directory, and do:

```
sudo make install
```

And it's just that simple.

---

### Post by heimo on 2005-07-30
[QUOTE=Ubunted]I had this problem myself. Here's the fix: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871]("https://bugzilla.ubuntu.com/show_bug.cgi?id=11871")

Download and extract "the patched and compiled version of gnome-app-install to solve the smeg-problem"

Then open a terminal in the extracted directory, and do:

```
sudo make install
```

And it's just that simple.[/QUOTE]

Great, thanks Ubunted! Also I'm glad to see that I was looking at the right place. :)

sophtpaw: If you can't get the problem solved with instructions from Ubunted and the link he posted, I'll be here to give step-by-step instructions.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=Ubunted]I had this problem myself. Here's the fix: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

Download and extract "the patched and compiled version of gnome-app-install to solve the smeg-problem"

Then open a terminal in the extracted directory, and do:

```
sudo make install
```

And it's just that simple.[/QUOTE]

Well, that is a step in the right direction. Whereas before i had nothing, i now have a list of apps, viz. Accessability, Accessories,  Graphics, Internet, etc etc. However, i still cannot open any of them. 

Has this been your experience?

---

sophtpaw

---

### Post by sophtpaw on 2005-07-30
[QUOTE=heimo]I don't know if it was really worth the trouble. ;D But at least I'll be able to find the same version of the file (tomorrow) and see if the problem is in it. I doubt, but you have to start somewhere. Thank you very much, I'll post you what I find.

Probably would be good idea to search other similar threads on this forum, if it's common problem, this may have been solved dozen times already.

Good night![/QUOTE]

Heimo,

that was alot of sweat! thx for the help. After all that some more help has finally come along. It nearly solved the issue, but i still can't open any of the apps. so, not quite there yet,

good nite,

sophtpaw

---

### Post by Ubunted on 2005-07-31
Well that solved it for me, I got no clue what's wrong now. :-?

---

### Post by heimo on 2005-07-31
Rinning the badly behaving application from terminal can reveal error messages. I'd try:
 ```
sudo python /usr/bin/gnome-app-install
```
... and watch the messages that appear on terminal.

---

### Post by Fummie on 2005-07-31
[QUOTE=heimo]Great, thanks Ubunted! Also I'm glad to see that I was looking at the right place. :)

sophtpaw: If you can't get the problem solved with instructions from Ubunted and the link he posted, I'll be here to give step-by-step instructions.[/QUOTE]
I could do with some help.  :-? 
Where do I type: sudo make install?

---

### Post by heimo on 2005-07-31
[QUOTE=Fummie]I could do with some help.  :? 
Where do I type: sudo make install?[/QUOTE]

Right click, choose Save Link As
[https://bugzilla.ubuntu.com/attachment.cgi?id=2836]("https://bugzilla.ubuntu.com/attachment.cgi?id=2836")
Choose to save it to your home folder

Open terminal (Applications->System Tools->Terminal)
Enter (or copy-paste*):
 ```

cd /tmp
tar xzvf ~/gnome-app-install-0+20050404a-3.tar.gz 
sudo make install

``` 

That should do it.

*) In X, easiest way to copy paste is just to highlight ("paint") the text , then middle-click to paste.

---

### Post by Fummie on 2005-07-31
[QUOTE=heimo]Right click, choose Save Link As
[https://bugzilla.ubuntu.com/attachment.cgi?id=2836]("https://bugzilla.ubuntu.com/attachment.cgi?id=2836")
Choose to save it to your home folder

Open terminal (Applications->System Tools->Terminal)
Enter (or copy-paste*):
 ```

cd /tmp
tar xzvf ~/gnome-app-install-0+20050404a-3.tar.gz 
sudo make install

``` 

That should do it.

*) In X, easiest way to copy paste is just to highlight ("paint") the text , then middle-click to paste.[/QUOTE]

You are a legend, thanks for your help.  :grin:

---

### Post by sophtpaw on 2005-07-31
[QUOTE=heimo]Rinning the badly behaving application from terminal can reveal error messages. I'd try:
 ```
sudo python /usr/bin/gnome-app-install
```
... and watch the messages that appear on terminal.[/QUOTE]

Hello Heimo,

back for some more  O:) 

i sudo'd python /usr/bin/gnome-app-install to see if, as you suggest, an error message, or anything might reveal something of use. Here is:

:~$ sudo python /usr/bin/gnome-app-install
Password:
Reading package lists... Done
Building dependency tree... Done
Got badly sized icon for gnome-util
Got badly sized icon for xmms_mini
Got badly sized icon for hwdb

let me know if it means something

sophtpaw

---

### Post by heimo on 2005-07-31
I actually get this, and it still works fine:
```
/usr/lib/gnome-app-install/AppInstall.py:88: GtkWarning: Theme directory mimetyp es48x48/apps of theme Humility has no size field

  gtk.window_set_default_icon(self.icons.load_icon("gnome-settings-default-appli cations", 32, 0))
Reading package lists... Done
Building dependency tree... Done
Got badly sized icon for web-browser
Got badly sized icon for xmms_mini
Got badly sized icon for hwdb

``` 

Hey! Just got an idea... Have you tried the small triangle shaped icon on the left side of those icons? Usability on this application is not probably the best... or it's not working as expected on my computer either. If I click on the names or icons, those don't open, I have to use the trianle.

---

### Post by sophtpaw on 2005-07-31
[QUOTE=heimo]I actually get this, and it still works fine:
```
/usr/lib/gnome-app-install/AppInstall.py:88: GtkWarning: Theme directory mimetyp es48x48/apps of theme Humility has no size field

  gtk.window_set_default_icon(self.icons.load_icon("gnome-settings-default-appli cations", 32, 0))
Reading package lists... Done
Building dependency tree... Done
Got badly sized icon for web-browser
Got badly sized icon for xmms_mini
Got badly sized icon for hwdb

``` 

Hey! Just got an idea... Have you tried the small triangle shaped icon on the left side of those icons? Usability on this application is not probably the best... or it's not working as expected on my computer either. If I click on the names or icons, those don't open, I have to use the trianle.[/QUOTE]

 \\:D/ 

what a brilliant idea!!!  :shock: 

What can i say. Its hard to fix something if it aint broke. Silly me. I thought one just clicked on the big words, and i never saw the small triangles which open up a tree to other more specific sub menus.

so, it is working now   

Thanks - you're a diamond geezer, as they say here,

--sophtpaw

--------------------------------------------------------------------------------------------------------------

"At first they laugh at you, then they fight you, then they join you"

---

### Post by heimo on 2005-07-31
:D Thanks!

---

