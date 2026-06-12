---
title: "garageband..."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by 006rocks on 2007-03-06
are there any programs like this for ubuntu?

---

### Post by 23meg on 2007-03-06
Check out Jokosher.

[http://www.jokosher.org](http://www.jokosher.org)

You'll almost certainly find more useful stuff here:

[http://www.linux-sound.org](http://www.linux-sound.org)

---

### Post by 006rocks on 2007-03-07
uhhh...how do u download and install that? like whats the command scrpit or whateever...or wheres the spot on there sight to download it...

---

### Post by dlai on 2007-03-07
There is a good description on their website under download [http://www.jokosher.org/download]("http://www.jokosher.org/download")
If you go to the part where it says "Installing Jokosher 0.2 on Ubuntu 6.10 Edgy or Ubuntu 6.06 Dapper", then you just have to follow their tutorial.

---

### Post by 23meg on 2007-03-07
There's a "Download" section on the top, in the navigation bar, which has instructions for installing under Dapper and Edgy.

---

### Post by 006rocks on 2007-03-07
all that stuff makes absolutly no sense to me...

---

### Post by AndyCooll on 2007-03-07
[Installing Jokosher 0.2 on Ubuntu 6.10 Edgy or Ubuntu 6.06 Dapper]("http://www.jokosher.org/download#ubuntu")

Essentially its saying that if you download that little script (mentioned in the above link) to your desktop, change its permissions and double click on it, that script will do all the work for you. It will look for the correct versions of dependencies and install them if they're not there.

And then once its all installed that script on your desktop becomes your desktop icon to start the program up.

:cool:

---

### Post by 006rocks on 2007-03-07
uhhhh, where/how do i download the run script? ( i feel so stupid...) i can find it on there websight...

---

### Post by 23meg on 2007-03-07
[http://www.jokosher.org/0.2/Jokosher0.2runscript](http://www.jokosher.org/0.2/Jokosher0.2runscript)

---

### Post by 006rocks on 2007-03-07
uhhhh...what and the hell does all that stuff meen? i dont get what im supposed to do...

---

### Post by 23meg on 2007-03-07
Right click it, choose "Save Link As".

---

### Post by 006rocks on 2007-03-07
ok...then what? i dont get what they r saying on there websight...i cant change anything under the permision tab...

---

### Post by 23meg on 2007-03-07
This is the box you should tick:

[IMG]http://i16.tinypic.com/49j4j5z.png[/IMG]

---

### Post by 006rocks on 2007-03-07
uhhh... i dont see that...i dont have that type of box...i dont have the last three options. also there is no scroll/list thingy to change the access...

---

### Post by 23meg on 2007-03-07
Right, this is what you should see when you do that. Click the checkbox, then click "Close" and then double click the file and wait a bit.

---

### Post by 006rocks on 2007-03-07
there is no check box!!! thats what im trying to say...

---

### Post by kevinlyfellow on 2007-03-07
Which version of Ubuntu are you running?

If its dapper, they have a different setup for that menu.  If you see 9 check boxes then check all the boxes that match up with 'execute'

If its not the case, maybe you could give us a screenshot

---

### Post by 006rocks on 2007-03-07
how do i take a screen shot?

---

### Post by kevinlyfellow on 2007-03-07
either hit the Print Screen Key (somewhere on the upper right hand corner of your keyboard) or under 'applications -> take screenshot'.  After thats, save it to your desktop.  Right click on it and open it it with 'gThumb image viewer' or 'the Gimp'.  Crop only what necessary.

Good luck :-)  I know this is a bit frustrating right now, but stick with it, because once you get the hang of it, it really is easy

---

### Post by old_geekster on 2007-03-07
> **006rocks said:**
> how do i take a screen shot?
Here is how you take a screenshot: click on Applications (lower left screen)/Accessories/Take Screenshot.

It will place a copy of whatever is on your screen at the time, on your desktop.

---

### Post by 006rocks on 2007-03-07
print screen button no worky...and i cant find anythign under applications that says pront screen or take screen shot or what ever,,,

---

### Post by 23meg on 2007-03-07
Open a terminal (Applications / Accessories / Terminal), copy and paste the code below and post the output here.

```
lsb_release -a
```

---

### Post by 006rocks on 2007-03-07
im getting some software to take a screen shot...so hold on...

---

### Post by 006rocks on 2007-03-07
here is what i see when i go to properties...[IMG]http://i156.photobucket.com/albums/t25/006rocks/Screenshot.png[/IMG]

---

### Post by kevinlyfellow on 2007-03-07
Sorry, I meant applications -> accessories -> take screenshot (pointed out by old_geekster).  Well, to be honest , I've never seen a menu like that, I'll check back in later to try and figure out why you have that menu.

In the meantime, try to go to applications -> accessories -> terminal and copy and paste (or type in) this command

```
sudo chmod 777 Desktop/Jokosher0.2runscript
sudo sh Desktop/Jokosher0.2runscript
```

If that spits anything out like an error message, let us know

---

### Post by 006rocks on 2007-03-07
terminal command line u told me to enter dosnt work...try to figure out what is wrong with the menu thingy...

---

### Post by kevinlyfellow on 2007-03-08
what does your terminal tell you? (just copy and paste it)

---

### Post by aysiu on 2007-03-08
If 006rocks is using Edgy, [*jokosher* is in the Universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=jokosh&searchon=name&subword=1&version=all&release=all).

---

### Post by kevinlyfellow on 2007-03-08
> **006rocks said:**
> terminal command line u told me to enter dosnt work...try to figure out what is wrong with the menu thingy...

BTW, I'm sure you don't mean anything by it, but you do need to be careful with what you say since no one can hear your 'tone of voice'.  Remember that we are not tech support, we are all just users trying to help each other out.  Thats why they call it a community :-)

---

### Post by kevinlyfellow on 2007-03-08
> **aysiu said:**
> If 006rocks is using Edgy, [*jokosher* is in the Universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=jokosh&searchon=name&subword=1&version=all&release=all).

HaHa, I just assumed that it wasn't, since the first suggestion was to use a shell script...   Any ideas on his properties menu???

---

### Post by kevinlyfellow on 2007-03-08
If you are using edgy eft (Ubuntu 6.10) then add the extra repositories as this website explains

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29)

then just open up synaptic package manager, (System -> Administration -> Synaptic Package Manager) and search for jokosher.  Click on the box and choose to install

[COLOR="Red"]EDIT  It seems that this won't be useful to you 006rocks, so just ignore it[/COLOR]

---

### Post by aysiu on 2007-03-08
> **kevinlyfellow said:**
> HaHa, I just assumed that it wasn't, since the first suggestion was to use a shell script...   Any ideas on his properties menu???
[Three weeks ago, 006rocks was installing 6.06, so I'm going to assume it's not Edgy](http://ubuntuforums.org/showthread.php?t=361396). We may need the script after all...

---

### Post by kevinlyfellow on 2007-03-08
> **aysiu said:**
> [Three weeks ago, 006rocks was installing 6.06, so I'm going to assume it's not Edgy](http://ubuntuforums.org/showthread.php?t=361396). We may need the script after all...

Thanks for the link, explains why the system is kinda funky.

---

### Post by aktiwers on 2007-03-08
Theres also Rosegarden. (google it)

---

### Post by aysiu on 2007-03-08
> **aktiwers said:**
> Theres also Rosegarden. (google it)
Rosegarden is in the Universe repositories, even for Dapper Drake.

---

### Post by 23meg on 2007-03-08
Rosegarden is much more sophisticated; a lot less Garageband-like than Jokosher though. And the version of Jokosher in Edgy Universe is older than what the script installs.

---

### Post by 006rocks on 2007-03-08
how do i get the more complex program? im gona try that...but still try to figure out y my oc wint let me jokosher....

---

### Post by Bwosc on 2007-03-08
You can find all the apps in the Synaptic if you have all the main repositories enabled.

If I may suggest another a bit more complex app, [Ardour]("http://ardour.org") w/ [Jack.]("http://jackaudio.org") (+ Hydrogen and lots of other stuff) That's what I use. It's very very cool although you might find it a bit intimidating at first.

---

### Post by kevinlyfellow on 2007-03-08
> **006rocks said:**
> how do i get the more complex program? im gona try that...but still try to figure out y my oc wint let me jokosher....

No one will be able to help you figure out why the jokosher script does not work until you tell us what the output of the terminal is when you do this
```

sudo chmod 777 Desktop/Jokosher0.2runscript
sudo sh Desktop/Jokosher0.2runscript

```

---

### Post by 006rocks on 2007-03-08
so i open terminal and copy and paste that whole thing?

---

### Post by kevinlyfellow on 2007-03-08
yes

---

### Post by 006rocks on 2007-03-08
this is what happens [IMG]http://i156.photobucket.com/albums/t25/006rocks/Screenshot-1.png[/IMG]

---

### Post by 23meg on 2007-03-08
Now double click the script and wait.

---

### Post by 006rocks on 2007-03-08
[IMG]http://i156.photobucket.com/albums/t25/006rocks/Screenshot-1-1.png[/IMG]
WTF!!!

---

### Post by kevinlyfellow on 2007-03-08
in your terminal, copy and paste
```
sudo aptitude -y install python-gnome2 python-setuptools cvs 
```

don't worry, you are almost done

after you've done this, try again

---

### Post by 006rocks on 2007-03-08
i just executed the script for it...now what do i do?

---

### Post by kevinlyfellow on 2007-03-08
I'm not sure if it puts an icon in your menus, but a sure fire way is by going to your terminal and typing in jokosher.  You can also do this with a run dialog or you can create an icon for it (I don't know xfce, so I can't help you with that)

btw, if you have questions about what exactly you did and why, be sure to ask

---

### Post by 006rocks on 2007-03-08
i entered the one thing that u told me...then i enterd the other thing...then i executed jokosher...it poped up this box, ran through some stuff, now what do i do?

---

### Post by kevinlyfellow on 2007-03-08
Does Jokosher work?  Do you mean that you got created a new project and you need help using the program?  Please be as descriptive as you can.

---

### Post by 23meg on 2007-03-08
Hit Alt + F2 and type "jokosher".

---

### Post by kevinlyfellow on 2007-03-08
Actually, I just installed it and in order to run it, you need to execute the script you installed with, so in other words double click on the Jokosher script

---

### Post by Patrick K on 2007-03-09
I didn't have any luck with Jokosher. I could never get it to record. I just use Audacity and Ardour.

---

### Post by 006rocks on 2007-03-09
jokosher is not working...and it says its not installed on my pc... whats supposed to happen when u  right click and press "execute" Jokosher0.2runscript

---

### Post by kevinlyfellow on 2007-03-09
> **006rocks said:**
> jokosher is not working...and it says its not installed on my pc... whats supposed to happen when u  right click and press "execute" Jokosher0.2runscript

Jokosher is suppose to run when you execute it

Since you say its not working, you will need to run the file via terminal so that we have any chance of figuring out whats going on.  Open the terminal and type in 
```
sh Desktop/Jokosher0.2runscript
```
If jokosher fails to run, Copy and Paste what the terminal outputs (error messages presumably) and post it up here.

---

