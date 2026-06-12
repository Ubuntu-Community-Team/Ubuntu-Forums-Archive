---
title: "Help Need to make a directory"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by hitspace on 2008-01-06
hey . im not exactly a total newbie to computers or ubuntu but i am very very unsure about whether i can actually do what i need to do without help. 

well im trying to get kaffeine player to play real media files . i downloaded the win32 codec 
to put it bluntly im stumped 

 my question how do i make a directory in usr/lib and name it win32 . if i just try making a folder in the usr/lib folder then it gives me an error saying i dont have permission .im hoping someone will have a command that i can use to clean up this whole mess .but really someone help me .  i doubt whether i know what im doing .

---

### Post by Redache on 2008-01-06
Can you give more information?

i.e. where did you get the Win32 Codec from because usually you can just use Add/Remove in the Program menu and select the Gstreamer plugins.

To clarify further why do you need to create a folder in /usr/lib?

If it's important to some instructions you've found you need to use the following.

```

cd /usr/lib
sudo mkdir win32
```

You need to prefix it with Sudo because write privileges in that folder is restricted to root, which is not available as a separate user on Ubuntu by default. If you ever get the same message try invoking Sudo to take root privileges.

---

### Post by dbbolton on 2008-01-06
you could do it like this:

```

cd /usr/lib
sudo mkdir win32

```

or, you could launch your file manager as root and do it graphically- but be very careful with root permissions.

---

### Post by mybeat on 2008-01-06
I dunno nothing about kaffeine,but to create a dir you can try "sudo mkdir win32".

---

### Post by philinux on 2008-01-06
you dont need to do any of that just type in a terminal

```
sudo apt-get install w32codecs
```

and it will be sorted.

---

### Post by jken146 on 2008-01-06
> **philinux said:**
> you dont need to do any of that just type in a terminal

```
sudo apt-get install w32codecs
```

and it will be sorted.

w32codecs are in the Medibuntu repository, so you'll need to add this first.  Instructions: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by philinux on 2008-01-06
> **jken146 said:**
> w32codecs are in the Medibuntu repository, so you'll need to add this first.  Instructions: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


good pickup.

---

### Post by hitspace on 2008-01-06
ya more info right
well i got the plugin codec thing win32 anyway from the mplayer website in the downloads section . i would love to hear how i could do it with add remove though for future reference anyway . 

what im trying to do is play real media and other heavily used windows file types . 
these are the instructions to what i was doing 


 How to : Play a real media file



Hi, to play a real media file you need this component. I have tested it on Ubuntu 7.10 before. This is the easy way I do it:

1. Install the Kaffeine player. To install just go to 'Synaptic Package Manager' and search for it. Then, 'Mark for Installation' to install the Kaffeine.

2. You need download the "essential codecs package" from MPlayer download page: [http://www.mplayerhq.hu](http://www.mplayerhq.hu)

3. Make directory name "win32" in the /usr/lib with your terminal. Please doing this section with root privilage. Its become /usr/lib/win32 .

4. Extract the "essential codecs package" that you have download before and copy all the contents to /usr/lib/win32 .

5. Open Kaffeine player. For the 1st time the kaffeine can't play the real media. This is because the codec is not define properly. What you can do is, just go to settings --> xine engine --> parameters --> decoder and type /usr/lib/win32 under the external Real Media codecs path. Now you can enjoy watching your real media file. Thats all.


win32 in mediubuntu is in the non free section , meaning i have to pay right .i dont know which codec i need to download either . 

secondly i got it(win32) or what i though was the  win32 codec on the mplayer website without paying .i would post the address but i cant find the place where i downloaded it . 

Posted by 

this is the address if you would like to look into it
[http://yourubuntulinux.blogspot.com/2007/12/how-to-play-real-media-file.html](http://yourubuntulinux.blogspot.com/2007/12/how-to-play-real-media-file.html)

---

### Post by philinux on 2008-01-06
why not just install realplayer

---

### Post by inaety on 2008-01-06
Step three can be accomplished through what everyone else is saying.  Just do 


sudo mkdir /usr/lib/win32

---

### Post by philinux on 2008-01-06
[http://www.real.com/linux/](http://www.real.com/linux/)

Real Player for linux

---

### Post by nowshining on 2008-01-06
u could of just isntalled gstreamer and stuff from add/remove or basically triied to play the file in mplayer to see if a pop-up asks u if u need certain plugins, u could of tried double-clicking it and if not mplayer - totem should ask to download the needed plugins if u try to play a title in there.

---

### Post by hitspace on 2008-01-06
sudo mkdir /usr/lib/win32

i put this into the terminal . a directory named win was made in usr/lib but when i try to copy the folder with the extracted codec it tells me i have no permission . help ? 

if i try to bypass this by directly extracting to the win32 file i get an error 

saying that it couldnt be done . when i look at the command line i get this . it seems like that permission thing is gonna make this really hard . 

tar: win32codecs-essential-20040703: Cannot mkdir: Permission denied
tar: win32codecs-essential-20040703/CLRVIDDC.DLL: Cannot open: No such file or directory
tar: win32codecs-essential-20040703/CtWbJpg.DLL: Cannot open: No such file or directory
tar: win32codecs-essential-20040703/LCodcCMP.dll: Cannot open: No such file or directory
tar: win32codecs-essential-20040703/acelpdec.ax: Cannot open: No such file or directory
tar: win32codecs-essential-20040703/alf2cd.acm: Cannot open: No such file or directory
tar: win32codecs-essential-20040703/asusasv2.dll: Cannot open: No such file or directory
.........
......
....


tar: Error exit delayed from previous errors

why didnt i install real player ? because when i download it and try to launch the exe  does nothing . would the file being downloaded to the desktop have  anything to do with it ?the instructions said to type this into the terminal 
chmod a+x RealPlayer10GOLD.bin (to make it an exe)
then
./RealPlayer10GOLD.bin (to run it )

i did . nothing happened . to be more specific . it said the file or directory doesnt exist . man i was beginning to like ubuntu , i hate it when programs are pain in the butt ..

---

### Post by philinux on 2008-01-06
Check my post , number 11.

you downloaded the windows version not linux.

---

### Post by hitspace on 2008-01-06
alright im going to tell you what happened ......
my god the suspense is killing me . 


....
.....
......

wow it tells me the exact same thing ... im feeling ;(

oh and philinux .i did download the linux one . and just in case . IF i had download the windows version it probably would have started when i turned it on through wine if you know what i mean :(

actually me being savvy or at least ... whatever point i did try playing the file in totem . of course the plugin thing came on and wow guess what it said when i confidently told it to go fetch the appropriate codecs. why , no matching codecs of course .imagine what happened to my teenage ego .

---

### Post by hitspace on 2008-01-07
is there nothing i can do ? i cant get real player to install and the codecs dont download . what should  i do ? i know other people have gotten real media to play on ubuntu is there any other method

---

### Post by philinux on 2008-01-07
Try this.

[http://ubuntu.org.ua/commercial/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://ubuntu.org.ua/commercial/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

Dont worry about it being feisty it install the dna helix plugins correctly. The gutsy version does not install the plugins to play streaming audio. It's a bug. It's been launchpadded.

---

### Post by hitspace on 2008-01-07
Do you mean i should install helix player ?

---

### Post by oldos2er on 2008-01-07
Did you download Realplayer to your desktop? If so you have to 'cd Desktop' before running ./RealPlayer10GOLD.bin

---

### Post by hitspace on 2008-01-07
yea i did so what is the whole code . where should i put the cd desktop line 

chmod a+x RealPlayer10GOLD.bin

./RealPlayer10GOLD.bin 

i put it in like this but it did nothing 

salaam@ubuntu:~$ cd Desktop
salaam@ubuntu:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
'salaam@ubuntu:~/Desktop$ '
> ./RealPlayer10GOLD.bin 
> 
>

err philinux i tried installing through the link you gave me . it says failed to install
terminal spat this out . 


(reading database ... 111008 files and directories currently installed.)
unpacking realplay (from .../realplay_10.0.9-feirsty1_i386(2).deb)...
dpkg: error processing /home/salaam/desktop/realplay_10.0.9-0feisty1_i386(2).deb
(--install):
trying to overwrite ' /usr/share/locale/zh_TW/LC_MESSAGES/libgtkhx.mo',which is
also in package helix-player 
dpkg-deb:subprocess paste killed by signal (Broken pipe)

---

### Post by oldos2er on 2008-01-07
" salaam@ubuntu:~$ cd Desktop
salaam@ubuntu:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
'salaam@ubuntu:~/Desktop$ '
> ./RealPlayer10GOLD.bin"

 If you get no feedback from the command, it worked. So now enter ./RealPlayer10GOLD.bin and press enter.

---

### Post by hitspace on 2008-01-07
salaam@ubuntu:~$ cd Desktop
salaam@ubuntu:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
salaam@ubuntu:~/Desktop$ RealPlayer10Gold.bin
bash: RealPlayer10Gold.bin: command not found
salaam@ubuntu:~/Desktop$ >./RealPlayer10GOLD.bin
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 
salaam@ubuntu:~/Desktop$ 

ya but isnt it supposed to do something ? like well i dont know start the exe install real player something along those lines ?

---

### Post by thelatinist on 2008-01-07
> **hitspace said:**
> win32 in mediubuntu is in the non free section , meaning i have to pay right .

No, that doesn't mean "free as in beer," but "free as in speech" (see [Gratis versus Libre]("http://en.wikipedia.org/wiki/Gratis_versus_Libre") and [Free Software]("http://en.wikipedia.org/wiki/Free_software"))  Which is to say, these codecs are not free open source software and may pose legal issues in certain countries.  But you don't have to pay to download them.

---

### Post by hitspace on 2008-01-07
ahh ok now about my problem what do i do ? and now totem movie player is also driving me crazy . all video playback is in black and white . any other suggestions .that work .

---

### Post by philinux on 2008-01-07
Ubuntu is based on debian hence .deb files

[http://ubuntu.org.ua/commercial/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://ubuntu.org.ua/commercial/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

Click the link to download this to your desktop or wherever 

double click it and it installs.

Nothing could be simpler.

---

### Post by oldos2er on 2008-01-07
> **hitspace said:**
> salaam@ubuntu:~$ cd Desktop
salaam@ubuntu:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
salaam@ubuntu:~/Desktop$ RealPlayer10Gold.bin
bash: RealPlayer10Gold.bin: command not found
salaam@ubuntu:~/Desktop$ >./RealPlayer10GOLD.bin
salaam@ubuntu:~/Desktop$ 

ya but isnt it supposed to do something ? like well i dont know start the exe install real player something along those lines ?

 Why is that ">" there? It shouldn't be.

---

### Post by nowshining on 2008-01-08
have u tried

sudo sh Realplayer10Gold.bin

:P

by the way to autocomplete names press the TAB key, if it doesnot auto complete then u'll need to put another letter as that means u got more choices than one to autocomplete.

Example

sudo sh Re (press tab key) 

equals

sudo sh Realplayer10Gold.bin

---

