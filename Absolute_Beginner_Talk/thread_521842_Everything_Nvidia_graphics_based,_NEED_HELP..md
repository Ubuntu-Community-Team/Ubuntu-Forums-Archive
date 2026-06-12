---
title: "Everything Nvidia graphics based, NEED HELP."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
ok, i have my drivers,, supposedly, thats what the pc said to me, so i said ok, and yeah, now where do i go to configure them? and, can i over clock my graphics card like i can on windows, and, can i configure a multiple display setup? cause right now my 27inch tv, is all scrambled looking,,

---

### Post by Jimmyfj on 2007-08-09
I use Sysinfo lokated in Programs>Add/Remove>System tools, (for install) (Programs>System tools>Sysinfo, for launch) to access the settings for my nVidia card. Don't know if you can overclock your GPU, never had the nerve to do that.

---

### Post by jake16424 on 2007-08-09
> **Jimmyfj said:**
> I use Sysinfo lokated in Programs>Add/Remove>System tools, (for install) (Programs>System tools>Sysinfo, for launch) to access the settings for my nVidia card. Don't know if you can overclock your GPU, never had the nerve to do that.

thank you for replying to my post,, and, i dont have a clue where tht is,, i got to the add remove then system tools,, but,, idk where to go from there,, shouldnt there just be like,, a setting or something somewhere to change? or a control panel? or some kind of interface?

---

### Post by RomeReactor on 2007-08-09
Hi. There's already a tool for configuring nVidia cards, **nvidia-settings**; press ALT+F2 and enter:
```
nvidia-settings
```

---

### Post by jake16424 on 2007-08-09
> **RomeReactor said:**
> Hi. There's already a tool for configuring nVidia cards, **nvidia-settings**; press ALT+F2 and enter:
```
nvidia-settings
```

WOW you rock,, can i get a hug? haha,, beasty,, ima have to remember that,, if i wait,,

can that work to run installers to?:confused::confused::confused:

---

### Post by RomeReactor on 2007-08-09
Do you mean if you can run command line installers by pressing ALT+F2? Yes, you could, but you should only run them from a terminal (Applications->Accessories->Terminal) since sometimes they ask questions, or output errors you can only see in the terminal; if you run an installer by pressing ALT+F2, you won't be able to see any questions or messages, so if something goes wrong, you won't know what it is.

Or were you asking something different?

---

### Post by EXCiD3 on 2007-08-09
Actually you may want to run nvidia-settings as sudo: ```
sudo nvidia-settings
```
in case you want save your changes to xorg.conf. Otherwise you will not have permissions and will have to change the settings everytime.

You CAN overclock your graphics card using nvclock. To install: ```
sudo apt-get install nvclock
```
After it is install you can configure your graphics card to over/underclock it. Just be careful as you could fry it... You will probably want to google "nvclock" or search the forums for more information. I have a laptop so overclock is a bit out of the question as it already gets up to 80 degress Celcius while gaming...

---

### Post by Kushkah on 2007-08-09
> **jake16424 said:**
> and, can i over clock my graphics card like i can on windows, and, can i configure a multiple display setup?

For overclocking you can do it two ways. You can either add this line:
```
Option "CoolBits" "1"
```
to the "Device" section of your xorg.conf file, then restart your xserver and go into nvidia-settings. There should be a section for Clock Frequencies.

Or you can get a program called nvclock, [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/) I prefer this way because it also includes fan control, if your card is supported but I think most nvidia cards are now.

Edit: Someone beat me to it :)

---

### Post by jake16424 on 2007-08-09
> **EXCiD3 said:**
> Actually you may want to run nvidia-settings as sudo: ```
sudo nvidia-settings
```
in case you want save your changes to xorg.conf. Otherwise you will not have permissions and will have to change the settings everytime.

You CAN overclock your graphics card using nvclock. To install: ```
sudo apt-get install nvclock
```
After it is install you can configure your graphics card to over/underclock it. Just be careful as you could fry it... You will probably want to google "nvclock" or search the forums for more information. I have a laptop so overclock is a bit out of the question as it already gets up to 80 degress Celcius while gaming...

yeah i usually only overclock in windows when i start having like imesh\limewire\firefox\movies playing\ music going, and utorrent, just to give me a bit more bandwidth,,

or ill overclock playing half life 2,, jsut to get out of the 10-15fps range,, but with everything on max,,, =) i have my cpu overclocked right now,, its a 2.2ghz, oc to 2.3310 its not much, but im just starting its a new one, so idk what it will let me do...

thaknyou very much,, u rock

---

### Post by RomeReactor on 2007-08-09
> **EXCiD3 said:**
> Actually you may want to run nvidia-settings as sudo:
```
sudo nvidia-settings
```
in case you want save your changes to xorg.conf. Otherwise you will not have permissions and will have to change the settings everytime.
That's correct; forgot about that...
> You CAN overclock your graphics card using nvclock. To install: ```
sudo apt-get install nvclock
```
After it is install you can configure your graphics card to over/underclock it. Just be careful as you could fry it... You will probably want to google "nvclock" or search the forums for more information. I have a laptop so overclock is a bit out of the question as it already gets up to 80 degress Celcius while gaming...
Also forgot about **nvclock**.

---

### Post by jake16424 on 2007-08-09
how do i manage the gpu speed? the sudo nvidia-settings doesnt work in terminal, it does, but not to get to the gpu adjuster thing... =\im a complete newb if you havent discovered it, :P,, haha,,

---

### Post by EXCiD3 on 2007-08-09
hey thats alright, couple months ago i was just like you. In order to manage your gpu speed you will need to run nvclock, not nvidia-settings. Nvidia-settings is only for configure monitors, etc. Nvclock will help you overclock your card. 

Actually you may need to install nvclock-gtk to use it: ```
sudo apt-get install nvclock-gtk
``` to get a graphical interface for it after you install nvclock.

If that doesn't work, you can always run Synaptic Package Manger and search for nvclock and install anything that sounds like you might need it. ;) Thats usually what i do... I searched the forums, and couldnt find too much info on overclocking using nvclock...

I do recall **[this]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/")** Howto mentioning nvclock. You can download a tar.gz of it here: [http://www.box.net/index.php?rm=box_v2_download_shared_file&file_id=f_59965428]("http://www.box.net/index.php?rm=box_v2_download_shared_file&file_id=f_59965428")
Just untar it, and open the html's up in your browser. Definitely read through it as there are tons of little tweaks that significantly improved Feisty's speed.

---

### Post by jake16424 on 2007-08-09
> **Kushkah said:**
> For overclocking you can do it two ways. You can either add this line:
```
Option "CoolBits" "1"
```
to the "Device" section of your xorg.conf file, then restart your xserver and go into nvidia-settings. There should be a section for Clock Frequencies.

Or you can get a program called nvclock, [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/) I prefer this way because it also includes fan control, if your card is supported but I think most nvidia cards are now.

Edit: Someone beat me to it :)

ahh, ok i want to go the difficult rout and edit that file,, how do i do it? cause this is the only way ima get intimate with this os,,, so hit me with it =)

PS: thank you again.:popcorn:

---

### Post by RomeReactor on 2007-08-09
Let's start by putting the option **Kushkah** mentioned in the previous page; we'll open a file called **xorg.conf** in a text editor (this file manages your display settings), but first we'll back it up. So, open a terminal (Applications->Accessories->Terminal) and enter the following:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
this will make a backup of "xorg.conf" called "xorg.conf.backup"; next:
```
gksudo gedit /etc/X11/xorg.conf
```
once the text editor pops up with the file, scroll down to "Section: Device" and add the following line
```
Option "CoolBits" "1"
```
**NOTE**: Don't change anything else!
save the file and close the text editor. Now we'll make an entry in the menus for **nvidia-settings**, so you don't have to use a command line to open it. Right-click on the top left menus (Applications Places System) and select "Edit Menus". Make sure the **System Tools** menu on the right pane is checked. On the left pane, highlight "System Tools" and on the left press **New Item**. You fill it out like this:

Type: Application

Name: Nvidia Settings

Command: gksudo nvidia-settings

Comment: (you can put here anything you want, or leave it blank)

Now, you can find **nvidia-settings** on **Applications->System Tools->Nvidia Settings**.

---

### Post by EXCiD3 on 2007-08-09
Oh nice, i never knew that option existed. :) Haven't spent enough time hacking Feisty...

**EDIT: Screw this tutorial, just read the above post, its better :(**

Ok now down to business. Modifying your xorg.conf:
1) Open Terminal
2) Type:```
sudo gedit /etc/X11/xorg.conf
```
or "sudo kate" if you use KDE/Kubuntu like me ;)
3)Scroll down to the Device section that contains the name for you Nvidia card, and add that option to the Device section. Save, then restart the Xserver by pressing Ctrl-Alt-Backspace. Now that option will apparently be enabled in nvidia settings.

Sounds like that guy's description says nvclock even includes fan speed control, which adding "CoolBits" "1" won't get you.

Lemme know how this goes, next time im someplace with highspeed internet i may try this out myself... I'm on my mom's comp using dialup at the moment... :(

---

### Post by jake16424 on 2007-08-09
PROBLEMO.
1. (gedit:9673): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by RomeReactor on 2007-08-09
Don't worry about that error message; it's a [low priority bug]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917") at the moment, which means the developers know about it. but since it's not serious, they haven't fixed it yet, opting to fix more serious bugs first.

---

### Post by jake16424 on 2007-08-09
> **EXCiD3 said:**
> hey thats alright, couple months ago i was just like you. In order to manage your gpu speed you will need to run nvclock, not nvidia-settings. Nvidia-settings is only for configure monitors, etc. Nvclock will help you overclock your card. 

Actually you may need to install nvclock-gtk to use it: ```
sudo apt-get install nvclock-gtk
``` to get a graphical interface for it after you install nvclock.

If that doesn't work, you can always run Synaptic Package Manger and search for nvclock and install anything that sounds like you might need it. ;) Thats usually what i do... I searched the forums, and couldnt find too much info on overclocking using nvclock...

I do recall **[this]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/")** Howto mentioning nvclock. You can download a tar.gz of it here: [http://www.box.net/index.php?rm=box_v2_download_shared_file&file_id=f_59965428]("http://www.box.net/index.php?rm=box_v2_download_shared_file&file_id=f_59965428")
Just untar it, and open the html's up in your browser. Definitely read through it as there are tons of little tweaks that significantly improved Feisty's speed.


ok, i used the  command that you gave me, it installed it,, now where do i go?

---

### Post by RomeReactor on 2007-08-09
It looks like it doesn't make an entry in the menus (just installed it and it's nowhere to be found. So you'll have to:
1.- Use ALT+F2 to enter **gksudo nvclock_gtk**
or;
2.- Make a menu entry yourself. If you choose to do this, right-click on the top left menus and select "Edit Menus". On the left pane, highlight the section you want to put the entry in, and on the right, select "New Item". Remember, the command to enter this time is **gksudo nvclock_gtk**.

---

### Post by jake16424 on 2007-08-09
thank you im now overclocked, but i do not see anything saying new item, on the left of the desired menu, =\

---

### Post by RomeReactor on 2007-08-09
**New Item** appears on the right:

---

### Post by jake16424 on 2007-08-09
> **RomeReactor said:**
> **New Item** appears on the right:

haha,, ^_^

---

### Post by RomeReactor on 2007-08-09
:-s That *is* odd! try running the menu editor from the terminal:
```
gksudo alacarte
```

---

### Post by jake16424 on 2007-08-09
> **RomeReactor said:**
> :-s That *is* odd! try running the menu editor from the terminal:
```
gksudo alacarte
```



WTF

Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.


thats ODD,, i put in my password,, and that came up then the window opened,, =\

---

### Post by RomeReactor on 2007-08-09
Remember, that message corresponds to a [bug while using gksudo]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917") to open graphical applications (for command line applications requiring administrator rights, use **sudo**). Nothing to worry about.

Did the **New Item** button show up this time?

---

### Post by jake16424 on 2007-08-10
> **RomeReactor said:**
> Remember, that message corresponds to a [bug while using gksudo]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917") to open graphical applications (for command line applications requiring administrator rights, use **sudo**). Nothing to worry about.

Did the **New Item** button show up this time?


:-(noperz

---

### Post by RomeReactor on 2007-08-10
Well, that's weird. Let's try something else:
right-click on your desktop and select **Create Launcher**. To fill it out:

Type: Application

Name: NV Clock

Command: gksudo nvclock_gtk

Comment: (leave empty if you want).

You could even add an icon, like [this one]("http://www.techaidmalta.com/images/icon_nvidia_shield.gif"); just download it to some place safe in your home folder, press the "No Icon" button in the launcher, press "Browse", and navigate to where you saved it.

Then you could drag it somewhere in your top panel (or bottom panel).

---

### Post by jake16424 on 2007-08-10
> **RomeReactor said:**
> Well, that's weird. Let's try something else:
right-click on your desktop and select **Create Launcher**. To fill it out:

Type: Application

Name: NV Clock

Command: gksudo nvclock_gtk

Comment: (leave empty if you want).

You could even add an icon, like [this one]("http://www.techaidmalta.com/images/icon_nvidia_shield.gif"); just download it to some place safe in your home folder, press the "No Icon" button in the launcher, press "Browse", and navigate to where you saved it.

Then you could drag it somewhere in your top panel (or bottom panel).


haha,, sweet, you rock, it worked,, good problem solving skillz,, 

i have one question

can you help me with my audio drivers??? pleeeaseee???
my pc is based on media,, ubuntu isnt going to last long on my machine, unless i can get my audio working,, i have a topic started,, should be rather eyeopening if you would rather cover it there.. thank you =)

---

### Post by RomeReactor on 2007-08-10
I don't know much about sound cards, but I'll  take a look.

---

### Post by jake16424 on 2007-08-10
> **RomeReactor said:**
> I don't know much about sound cards, but I'll  take a look.

thankyou ,, thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou


ok, this is the error i get when i follow what they say todo in the readme file after i extract the files.

jacob@jacob-desktop:~$ ./realtek-linux-audiopack-3.5-6/
bash: ./realtek-linux-audiopack-3.5-6/: No such file or directory
jacob@jacob-desktop:~$




[CENTER][SIZE="5"]readme file says this[/SIZE]
Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.9b_1.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.9b_1.
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	[/CENTER]

---

### Post by man_bash on 2007-08-20
Hi, I have followed the thread and found it EXTREMELY useful (special thanks to RomeReactor for providing useful answers), but I have a question now.  I cannot edit the locked pipelines of my 6800XT card, I know I can enable 1 extra quad of pixel shaders, and 2 vertex shader pipelines. When I tried enbling extra vertex pipelines I actually disabled all but one of them. 
I used "nvclock -V 2 -f" command, and only my "Vertex unit 1" was now enabled, instead of 0, 1, 2,  & 4.
 How would the terminal command to enable all of them? I tried "nvclock -V 1 2 3 4 5 6 -f hoping to enable them all, but only "Vertex unit 0" became enabled. 

I have a NV40 core with 16 available pixel pipelines and 6  available vertex pipelines, with 8 PS and 4 VS units enabled.

---

### Post by jake16424 on 2007-11-02
wow... your allready about a million years ahead of me using the terminal, O_o

I'm reading a tutorial here and there about python GUI interface command's and programming,, but its long tedious and wow,,,, so yeah..

good luck sorry no one has had a answer. =-(

---

