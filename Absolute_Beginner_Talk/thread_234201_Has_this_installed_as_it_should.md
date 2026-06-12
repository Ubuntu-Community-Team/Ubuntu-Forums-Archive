---
title: "Has this installed as it should"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by cooper on 2006-08-11
Hi Guys,

Im a total noobie to Linux, and have just run the lastest release of ubuntu sever on a old pc to play around with.

This i am hoping will be put on two servers that i have at a school i work at.

Both to become file servers.

After the intsallation the cd was ejected and the setup completed.

All i get is a dos looking screen. Is this ok 

Where is the desktop???

Thanks for any help given, :confused:

---

### Post by jincast90 on 2006-08-11
> **cooper said:**
> Hi Guys,

Im a total noobie to Linux, and have just run the lastest release of ubuntu sever on a old pc to play around with.

This i am hoping will be put on two servers that i have at a school i work at.

Both to become file servers.

After the intsallation the cd was ejected and the setup completed.

All i get is a dos looking screen. Is this ok 

Where is the desktop???

Thanks for any help given, :confused:

I belive the server install, doesent come with any desktop enviorment. I should download one of the live cds, and install it from there. Or maybe you can downloade it using some commands, but I think this is a bad idea if ur a new.

---

### Post by Perfect Storm on 2006-08-11
If you choose Server install, there won't be any Desktop. The main reason for running server without a Desktop envoriment is to use all resources on running the server and not wasting the power on Desktop/gui stuff.

---

### Post by Jjohn on 2006-08-11
Hi Cooper,
         I do not think that the server comes with a desktop so everything is command line.
          If you want a desktop it may be better to not choose server option. That is my two cents worth
John

---

### Post by cooper on 2006-08-11
Thanks for the quick reply.

If this ubuntu server dosent have a desktop front end could anyone recommend a easy linux server for me to use.

---

### Post by orb9220 on 2006-08-11
I believe yes the server version does not install a gui window manger by defualt.

If want one for just doing configs and browseing and such then a light one like xfce4,fluxbox,fvwm.etc. 

You can also install gnome,kde etc but are considered more heavy.

Just check them out after you fiqure out what you need to do in a gui.

Hope this helps.
Good Luck

---

### Post by Perfect Storm on 2006-08-11
You can install Desktop upon the server install (if you have internet connection):
```
sudo apt-get update && sudo apt-get upgrade
sudo aptitude install xubuntu-desktop
```
(gives XFCE which will go nice if you want to use the computer as server with gui).

---

### Post by cooper on 2006-08-11
I have a intranet running from our windows 2003 server and want to move it onto a seperate server.

Also i am imaging all the school workstations and want to have a server with all the images.

---

### Post by cooper on 2006-08-11
Cool cheers for that.

Im downloading the XUbuntu alternate version as the server i will be using have raid hardrives.

Couldnt get internet connection to make the upgrade so waiting for a new download.

Will give it a go in a old workstation later.

Thanks alot for the help guys, this is a great forum and im sure i will be back soon being a Absolute Beginner.

Oh well back to sorting out microsoft computers.

:p

---

### Post by scheuri on 2006-08-11
Hi there...

The word "server" is sometimes a wee bit misleading.
Let me try to explain it in my words (which may not necessarly be the perfect ones).

A Server is a computer (whatever hardware) which offers server-services (webserver, fileserver, printserver, etc.).
You may use an old (desktop) computer to offer such services or even server-scale hardware.
However, on a productive server you very rarely find any kind of GUI. Most of them working with the shell which you described as "dos-like".

There is nothing wrong by using a GUI (XFCE, Gnome, KDE or whatever) on a server, it is just that a server is meant to use its ressources for the server-services instead of the GUI and the more software you installed the more security risk MIGHT occur.

So, for testing...no worries to install XCFE (which is lightweight and therefore probably a good choice). Even if you make that computer a prodcutive server you are not forced to uninstall the GUI.

That said, you may now understand why there is no GUI on the Server-CD of Ubuntu. It is just not common and this CD installs just the necessary stuff to run a server.
However, it is easy to post-install everything by using "aptitude".

Hope that helped.
Have fun
scheuri

---

### Post by cooper on 2006-08-14
Hi ive reinstalled and put Xubuntu server on.

Put the command 

sudo apt-get update && sudo apt-get upgrade

and get 

"Cannot write to "sudo apt-get update" (press RETURN)

Press return and.

Manual page sudo_root(8) line 92/120 (END)

---

### Post by Perfect Storm on 2006-08-14
try with aptitude instead of apt-get. (use it the same way)

---

### Post by cooper on 2006-08-14
Thanks for that it looked like it worked.

Started to run and i put the second command in thn had to put the CD in

But after that im back waiting for a command with no GUI

Rebooted and no GUI

Is there a start command i need to enter?

---

### Post by Perfect Storm on 2006-08-14
try with 
```
startx
```

---

### Post by cooper on 2006-08-14
tried startx and get  "command not found"

So ive tried to re-insstall and get

unable to fech some archives maybe run apt-get update or try with fix missing

---

### Post by Perfect Storm on 2006-08-14
Hmmmm.did you check if the CD you burned are okay?

Try this: [http://doc.gwos.org/index.php/DesktopUIDapper](http://doc.gwos.org/index.php/DesktopUIDapper)

---

### Post by cooper on 2006-08-14
when i get to command

sudo apt-get install xubuntu-desktop wdm 

I get E: couldnt find package data wdm

so im downloading xumbuntu again.

Im going home soon so will leave this downloading and will burn a new disk in the morning and try again.

Not far from getting there im sure.

Thanks for all the help your giving AI

cooper :D

---

### Post by Perfect Storm on 2006-08-14
wdm is in the universe in your sourcelist. 

command:
```

sudo nano /etc/apt/sources.list
sudo apt-get update
```

remove the # infront of the lines (except where there's two of them (##)).

Save, Exit and run the last command.
save = <ctrl> + <o>. Exit = <ctrl> + <x>

---

### Post by cooper on 2006-08-15
ok i lost again

i put in 

sudo nano /etc/apt/sources.list


i can see any # on the screen

---

### Post by Perfect Storm on 2006-08-15
give me a 
```
cat /etc/apt/sources.list

```

Does anything shows up?

---

### Post by cooper on 2006-08-15
no nothing happened there mate

---

### Post by Perfect Storm on 2006-08-15
Strange....

Well. Try download Xubuntu and make a new CD.

---

### Post by cooper on 2006-08-15
Ive just burnt a xubuntu desktop cd and put that in bios set to boot from cd.

It started a installation then opened up a desktop but the keyboard and mouse didnt work.  strange

downloading 

Alternate install CD  again

will let you know how i get on once its downloaded

---

### Post by cooper on 2006-08-15
Cool got it to work at last.

I feels like its running a bit slow, the mouse is a bit jumpy

Just need to get this on the network now and get my server to see a shared folder.

Thanks alot AI

---

### Post by Perfect Storm on 2006-08-15
What's the specs of the server? We might be able to getting it work better. Does it have a 3D graphic card? Even a small tnt can make it snappier in responds if you install nvidia drivers.

---

