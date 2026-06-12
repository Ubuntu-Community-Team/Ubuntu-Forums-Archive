---
title: "help with games"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-20
ok, i finally installed wine for edgy (witch was an exciting task with all those incredibly thorough instructions), but whenever i try to run a game (.exe) it seems like its starting, but then ubuntu restarts. it goes back to login screen(btw, is it possible to remove the login?). i have tried it on warcraft 3 and roller coaster tycoon 3. both do the same thing. idk for sure if wine sipports them, i couldnt find a list or anything, but they seem like common games that wine would support. And when if you respond with some sort of code or anything, keep in mind i am a total noob to linux, and i came from windows.



i tried dapper before, and it didnt require me to install drivers, everything was up to speed. but on edgy, it seems like drivers are not installed, it has incredible screen tearing when i scroll or move a window. this might be the problem with the games, idk. but its getting anyoing, and i would like to know wats up. i have my driver disk, but it wont red the aoutostart (it says fail). and i cant install individually, b/c i dont rlly understand the contents of the disk.


last thing, if i were to plug this hard drive into a computer (as slave), is it possible to red it from windows(wich is on the master) because i wanted to transfer a movie file to this hard drive (with ubuntu on it). i pluged it into another computer wich uses windows, but it did not red it in my computer. 



ok, THIS is the last thing. are there any mac emulators for linux? because i would like to install mac itunes. (i dont like fat32 winpods, i prefer +htf(i think thats wat it is) macpods. they are easier for ilinux)

---

### Post by gustolove on 2006-11-20
yes it sounds like a driver issue because the one that comes with the edgy doesn't support 3d rendering... u need to install the correct driver for your card... 

do you have nvidia or ati?

---

### Post by Cardmaster91 on 2006-11-20
i have nvidia, its integrated into the motherboard.

---

### Post by gustolove on 2006-11-20
try this command:

sudo apt-get install nvidia-glx

^^that should install the nvidia drivers

---

### Post by Cardmaster91 on 2006-11-20
that raised another question. when i try too use the "su" command, it asks for password, so i put in password, and it says 


su: Authentication failure
Sorry.



i forget wat i was reading that said to do this, but it got me annoyed and i had to stop. wen i used that command for nvdia install, the password worked (THANK GOD). i know u have to keep ur cool wen it comes to computers, but sometimes its tough.


idk if the driver installed, it still all jumpy, im gonna restart

---

### Post by MasterOfDisaster on 2006-11-20
You also have to run 'sudo nvidia-xconfig' to enable the drivers.

---

### Post by Marquis_de_Carabas on 2006-11-20
Just because a game is common doesn't necessarily mean it will work under Wine. Check out the [Wine Application DB]("http://appdb.winehq.org/"), it will tell you whether they work 'out of the box' or not, and what you need to do to get them working if not.

If you want a simpler way of playing Windows games then you might want to check out Cedega. You have to pay for it (three quid a month, or something like that) but it puts a relatively simple GUI around everything and apparently has better support for copy protection, 3d acceleration etc.

Don't expect too much though. Cedega and Wine are great projects, but not every game will be playable. I buy Linux versions whenever available (the more people buy them the more inclined manufacturers will be to release Linux versions of future games) and dual-boot for the rest. It's annoying, but I like my Morrowind.

---

### Post by CatKiller on 2006-11-20
> **Cardmaster91 said:**
> it seems like its starting, but then ubuntu restarts. it goes back to login screen

That doesn't sound good. Out of interest, what happens if you open a terminal and type **glxgears**?

>  i have tried it on warcraft 3 and roller coaster tycoon 3. both do the same thing. idk for sure if wine sipports them, i couldnt find a list or anything,

[Wine's Application Database]("http://appdb.winehq.org/")

> but they seem like common games that wine would support.

[Warcraft III entry]("http://appdb.winehq.org/appview.php?iAppId=897")
[Roller Coaster Tycoon 3 entry]("http://appdb.winehq.org/appview.php?iAppId=2600")

>  And when if you respond with some sort of code or anything, keep in mind i am a total noob to linux, and i came from windows.

A lot of people are. But the command line is still the most concise way to give instruction.

>  i have my driver disk, but it wont red the aoutostart (it says fail). and i cant install individually, b/c i dont rlly understand the contents of the disk.

As you've already discovered, you need Wine to run Windows applications. Not that I'm saying you should install Windows drivers with Wine, obviously. Use gustolove's instruction.

> last thing, if i were to plug this hard drive into a computer (as slave), is it possible to red it from windows(wich is on the master) because i wanted to transfer a movie file to this hard drive (with ubuntu on it). i pluged it into another computer wich uses windows, but it did not red it in my computer.

You can read Windows drives in Ubuntu. See [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows") and [here]("http://psychocats.net/ubuntu/mountwindows").

You might also want to read [these]("https://help.ubuntu.com/community/RootSudo") [pages]("http://psychocats.net/ubuntu/permissions").

---

### Post by Cardmaster91 on 2006-11-20
gustolov, and masterofdisaster 

I LOVE YOU. this is the first real, stright forward help that works on the fisrt try ive ever had on ubuntu. the driver works, and i can play games now, ty much.[http://ubuntuforums.org/member.php?u=3576](http://ubuntuforums.org/member.php?u=3576)

---

### Post by gustolove on 2006-11-20
love me long time... its good to hear that i helped :-D

---

### Post by Cardmaster91 on 2006-11-20
gustolove, and Marquis_de_Carabas

I LOVE YOU. this is the first real, stright forward help that works on the fisrt try ive ever had on ubuntu. the driver works, and i can play games now, ty much.

catkiller, thank you for those links. i took a peak, they seem pretty useful.



and i wopuld luv to use cadega, but dont u have to pay money monthly? my parents wont let me use the credit card.

---

### Post by Cardmaster91 on 2006-11-20
im trying to add warcraft 3 onto my panel, but it says 

Failed to execute child process "/home/tony/.wine/drive_c/Program
(no such file or directory)


i tried putting undersores for all the spaces, but still has similar error.



when i do run wc3, some of the text doesnt show. i dl the tahoma.ttf into drive_c/window/fonts, but certain text stil doesnt show. mostly capitals. and then, when i try to ceonnect to battle.net, it wont let me click on the password box. i cant type anything in.     but i g2g to bed. cyall tommora

---

### Post by gustolove on 2006-11-20
the . in the directory line is there because its hidden i believe... 

also... have u tried using the TAB key to get to the PW box for battlenet

---

### Post by Cardmaster91 on 2006-11-20
if i remove the . it still doesnt work. and yes ive tried tab

---

### Post by CatKiller on 2006-11-20
> **Cardmaster91 said:**
> i tried putting undersores for all the spaces, but still has similar error.

You should "escape" spaces and other control characters with a \, like so:
**~/.wine/drive_c/Program\ Files/...**

You'll see the path if you run it in a Terminal and use Tab to complete the path and filename.

I **think** you can use **wine "C:\Program Files\..."** although I've never tried it.

---

### Post by Cardmaster91 on 2006-11-20
umm, the \ didnt work, it returned same error. but now i have new problem. my sound isnt working on some games. i dont think i installed the drivers, if u could tel me how, that would be appreciated. i have realtek alc. and im using  harmon/kardon speakers.

---

### Post by Marquis_de_Carabas on 2006-11-20
Try the GUI way. Open Nautilus up and navigate to the relevant folder (you'll need to View=>Show Hidden Files to see the .wine directory) and find the program executable. Right-click, select "Make link" and then drag that link to your panel.

[Edit: Actually, you can probably skip the "Make link" step, just dragging the executable should work fine]

[Edit 2: Forget that, it doesn't work (Sorry; it's been a long day). Escaping the space doesn't work, enclosing the whole thing in quotes doesn't work. CatKiller's second suggestion, however, does work. The command for the PokerStars launcher I just created is: ```
wine "C:\Program Files\PokerStars\PokerStars.exe"
``` Try it like that (make sure to use backslash rather than forwardslash) and it should work fine.]

As for the sound, if it's working on some things then it doesn't seem like it would be a driver problem. Check the Apps DB for any mention of sound issues with those particular programs, and maybe change some of the settings in winecfg (change from Alsa to OSS or vice-versa). I'm just guessing here, but it can't hurt to try.

---

