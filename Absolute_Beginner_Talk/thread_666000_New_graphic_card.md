---
title: "New graphic card"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by joedirt313 on 2008-01-12
Good evening everyone, I just have a quick question to ask since I am new to linux(a couple of months) I have a vaio dual booting with windows xp and feisty fawn both on separate hd's works perfect. I bought a new graphics card and I want to install it Now I know the windows side of the house wont give me any probs on the install part but I am wondering if ubuntu would give me any probs will it pick it up or would I have to manually install it in ubuntu? and if so how to ?

Graphic card is 
Vision tek (ATI RADEON)
AGP Slot 
256 mb ddr2 Ram 
HD 2400 pro


Sorry For the double post my mistake

---

### Post by Fred_E _krugar on 2008-01-12
Are you using Envy to install the graphic drivers??

---

### Post by joedirt313 on 2008-01-12
Thats the thing I havent started at all cause I did not want to Start swapping cards w/o knowing the damage I may do prior and then F... myself. So I guess no so far......

---

### Post by szymon_g on 2008-01-12
hm.
after changing graphic card you won't be able to run a X's (not without some changes). after you get xorg's errors, pres alt+f2, login and type:

sudo killall -9 gdm

(that will 'kill' gdm)

than sudo dpkg-reconfigure xserver-xorg
follow it and choose ati driver.

personally, i'd buy an nvidia's card. much better support on linux

---

### Post by RomeReactor on 2008-01-12
Hi. Try going to 'System->Administration->Restricted Drivers Manager' and enable your card's drivers there.

EDIT: Too slow...

---

### Post by joedirt313 on 2008-01-12
Ok Well it seems its more of a trial and error thing with this so I will see what happens worst come to worst I will resolve any issues by posting with my girls laptop if my desktop doesnt work out the way I want it to lololo......

---

### Post by joedirt313 on 2008-01-13
Morning one and all 
As to follow up with my post I installed my graphic card got it up and running on windows d/t my dual boot no prob. Went to restart and run my ubuntu but now all I get is a command prompt type interface no longer my pictures or regular desktop interface, so what do I do??????

HELPPPPPPPPPPPP

---

### Post by overdrank on 2008-01-13
> **joedirt313 said:**
> Morning one and all 
As to follow up with my post I installed my graphic card got it up and running on windows d/t my dual boot no prob. Went to restart and run my ubuntu but now all I get is a command prompt type interface no longer my pictures or regular desktop interface, so what do I do??????

HELPPPPPPPPPPPP

Hi and as posted earlier use the command to reconfigure your xorg ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by joedirt313 on 2008-01-13
I saw the post and tried typing that in the command line and it didnt do anything. Cant tell you exactly what it did would have to restart and try it again. then restart and post the results.

---

### Post by joedirt313 on 2008-01-13
I typed in the command and it says: dpkg-reconfigure must be run as root
So what do I do ?

---

### Post by joedirt313 on 2008-01-13
Can anyone assist with the above question

---

### Post by RomeReactor on 2008-01-13
As **overdrank** said, run it with administrator privileges by prefacing the command with **sudo**:
```
sudo dpkg-reconfigure xserver-xorg
```
Accept all the defaults except when asked which video driver to use, choose **fglrx**.

---

### Post by joedirt313 on 2008-01-13
Ok 
when I type the sudo command killall this is what I get
Kill [option]...[--] name
killall-L,--list
killall-v,--version

when I type in the command dpkg config this is what I get
dpkg:conflicting action -E(-control) and -R(--remove)

have the slightest idea what any of that means or where to go from there to where it let me choose the drivers I need.....

---

### Post by overdrank on 2008-01-13
> **joedirt313 said:**
> Ok 
when I type the sudo command killall this is what I get
Kill [option]...[--] name
killall-L,--list
killall-v,--version

when I type in the command dpkg config this is what I get
dpkg:conflicting action -E(-control) and -R(--remove)

have the slightest idea what any of that means or where to go from there to where it let me choose the drivers I need.....

Ok let me start off by saying that I have not had the pleasure of using that card so I may not be of much help. Why did you try the kill all command before you used the configure command?

---

### Post by joedirt313 on 2008-01-13
Thats the advice someone had given on the post for installation of the drivers.(page 1) 
He said it had something to do with stopping some other running programs. 

But as to what it did which was prettie much nothing I tried to do the command dpkg.which gave me what I posted and even w/o running the killall it still gave me the same.
Well as for the card its reall just a 
ati radeon
nothing special just a newer model 
if need be I can tell you the chipset and all other needed info on it
but I was just trying to at least get it running with my ubuntu setup but cantget past the command code screen on startup

---

### Post by overdrank on 2008-01-13
> **joedirt313 said:**
> Thats the advice someone had given on the post for installation of the drivers.(page 1) 
He said it had something to do with stopping some other running programs. 

But as to what it did which was prettie much nothing I tried to do the command dpkg.which gave me what I posted and even w/o running the killall it still gave me the same.
Well as for the card its reall just a 
ati radeon
nothing special just a newer model 
if need be I can tell you the chipset and all other needed info on it
but I was just trying to at least get it running with my ubuntu setup but cantget past the command code screen on startup

Ok I reread the thread, I understand it that you swapped graphics cards? This was not a integrated graphics on the motherboard right? What was the previous model of  the card and did you uninstall it's drivers before the new graphics card?

---

### Post by joedirt313 on 2008-01-13
yes this is a new graphic card the previous was an nvidia graphic chip set intergrated and yes prior to installing the new card I uninstalled the drivers through windows. Not in the Linux boot, Does that make a diff?
I am duall booting windows on one hd and linux on another

---

### Post by overdrank on 2008-01-13
> **joedirt313 said:**
> yes this is a new graphic card the previous was an nvidia graphic chip set intergrated and yes prior to installing the new card I uninstalled the drivers through windows. Not in the Linux boot, Does that make a diff?
I am duall booting windows on one hd and linux on another

Ok yes this could be an issue. When installing did you disable the onboard graphics or is it auto detected? You may try what was suggested in the reply of the command -R. As I have never seen that reply using that command. Maybe someone with more experience will drop in and help.

---

### Post by joedirt313 on 2008-01-13
Well thats the thing when I went to run ununtu It automatically detected that I changed the card but went to the command type screen. 
and I guess I will keep my fingers crossed

---

### Post by overdrank on 2008-01-13
> **joedirt313 said:**
> Well thats the thing when I went to run ununtu It automatically detected that I changed the card but went to the command type screen. 
and I guess I will keep my fingers crossed

Ok just for grins  try this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then try the command startx

---

### Post by joedirt313 on 2008-01-13
Well I went and tried messing with some stuff ( great way of getting things to work )
and tried retyoping the dpkg command and it gave me something more promising is said:
type dpkg for help about installing and deinstalling packages use "deselect" or "aptitude" for package user-friendly management.

Anyone know what that mean
And drank I will try that command code once we know what I just posted does not make sense lololololol and thanks for the help

---

### Post by joedirt313 on 2008-01-14
Well for anyone wondering and for the purpose of settling any ffuture question as to what can be done, I eventually just erased my whole linux partition on the second hd and reloaded it again. Dont know if it is picking up my new gpu but I can at least see what I am doing(lololol) I will have to check to see if all the drivers are loaded correctly and it is working properly.thanks anyone for the time and effort in helping through this.

---

