---
title: "Need help with installing a program."
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-04
Hi

I want to trie a program that I found for Linux; [http://www.through-the-lens.net/cms/index.php?page=Download](http://www.through-the-lens.net/cms/index.php?page=Download) 

I have downloded the file to the desktop, it is a bin file(?). How do I install it?

On the page it stands this guide:
Linux installation - Just run the downloaded file as follows : 
sh ./install.bin

I have tried this, but with no luck.. And I am at the "Desktop" in the terminal. 

Thanks for all help.

---

### Post by Ecthelion on 2006-11-04
If it was a bin when you downloaded it, then you probably will have to change the permissions of it...

What do you get when you do 
```
sh ~/Desktop/install.bin
```
?

Isn't there a message that says something about permissions?

---

### Post by Oki on 2006-11-04
Hi Ecthelion

Thank you for your help:-)

What happened? Magic, the installation guide started. How could you know the code to run? What would happened if there was more then one bin files on my desktop?

Anyway, I am trying different photo programs to se if Linux could replace my Windows os, but this program was not what I thought it would be. Do you know how I can uninstall it?

Thanks!

---

### Post by taurus on 2006-11-04
```

cd ~/Desktop
sudo ./install.sh

```

---

### Post by Portable_Jim on 2006-11-04
> Do you know how I can uninstall it?

Have you tried Synaptic:
1. Go to the System menu then Administration -> Synaptic Package Manager.
2. Insert your / root password (whichever is asked for).
3. Click the "Serch" button.
4. Type in the name of your program (eg, Magic)
5. Click O.K (and wait)
6. Find the program in the list the comes up.
7. Right click in the square icon (in the first column and should be green)
8. Click the "Mark for removal" menu item.
9. Click the "Apply" button and click the "Apply" button again in the window that pops up.
10.Wait.
11. When it is done, close the window.

This might work, I am not too sure about it though. Please tell me how it goes if you try it.

---

### Post by Oki on 2006-11-05
Thank you very much for the good explanation Portable_Jim; just what we “Windows people” needs in the beginning:-D 
I didn't not find the program in Synaptic or in the add/remove application, but it was installed in a folder called Constructor 2.0. And to my surprise there was an uninstall option there(!). So now its gone.

I think there is one thing Linux could be better at, witch is to make icones in the applications menu or the desktop when installing new programs. 

Thanks all for your kind help:-)

---

### Post by Oki on 2006-11-05
I was hoping you could help me with another problem. 

I have downloaded a program called LightZone, and unpacked it on the desktop. The program works fine(very good one!), but I dont want it to be on the desktop. So, how do I move the folder with the program over to /opt (isn't this a ok folder for “other programs”)? I cant copy/paste with the mouse(properly since I am not Sudo). 

Thanks again

---

### Post by Ecthelion on 2006-11-05
> was hoping you could help me with another problem.

I have downloaded a program called LightZone, and unpacked it on the desktop. The program works fine(very good one!), but I dont want it to be on the desktop. So, how do I move the folder with the program over to /opt (isn't this a ok folder for &#8220;other programs&#8221;)? I cant copy/paste with the mouse(properly since I am not Sudo).

Thanks again

If it wasn't a lot of work installing it, then it would be easy to uninstall it an install it back in the right folder.

You can use your ~/ folder to install it to...
Then it's not in your way and still not hard to find back too

---

### Post by CatKiller on 2006-11-05
> **Oki said:**
> I think there is one thing Linux could be better at, witch is to make icones in the applications menu or the desktop when installing new programs.

It's because you're installing programs in a freaky way, relatively speaking. If you install applications with Synaptic, which is both easy and well-supported, you'll get icons in the menu for most graphical applications. Downloading stuff off the Internet is not really a "Linux" experience - heck, it's not even an "Ubuntu" experience - to be able to judge whether it does it well or poorly.

---

### Post by Ecthelion on 2006-11-05
> It's because you're installing programs in a freaky way, relatively speaking. If you install applications with Synaptic, which is both easy and well-supported, you'll get icons in the menu for most graphical applications. Downloading stuff off the Internet is not really a "Linux" experience - heck, it's not even an "Ubuntu" experience - to be able to judge whether it does it well or poorly.

I don't really agree...
I think it's great to compile packages from source etc... It's something that is easily done in Ubuntu (I think that) and I find it very Linux- or even Ubuntu alike.

It's just that no-one expects an average user to do it that there aren't links for everything. And for someone who likes to install everything to see what it is, it's not a problem to make a link yourself...

... And that still is a lot Ubuntu-alike (or that's my opinion, but I know I would never have tried stuff like that if I still were on windows...)

---

### Post by kylevan on 2006-11-05
> **Oki said:**
> I think there is one thing Linux could be better at, witch is to make icones in the applications menu or the desktop when installing new programs. 

Thanks all for your kind help:-)

I recommend that you use either Add/Remove Programs from the application menu, or else Synaptic from the system>administration menu for installing programs.  both of these will make uninstallation much easier, as well as automatically placing icons in the menus.

Have you checked out F-spot?  It's an open-source equivalent to Google's Picasa.  Alternatively, Picasa is also available for Linux.  Both are available through Synaptic.

Also, try reading this page... [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)  "How to install ANYTHING in Ubuntu" is the title... should be helpful.

---

### Post by Oki on 2006-11-05
Hi CatKiller
I should have written more precisly; when I was whining about the missing icons I did not mean the Ligtzone or Constructor 2.0(witch is not in synaptic btw). But I thought about programs like Gnucash and others that I installed via Synaptic, witch never showed up on the desktop or in the Applications menu. I had to find the “Run” file myself and make shortcuts to them in the Applications menu. Belive me, this is not so easy for a newbie coming from Windows! But on the other hand, I have learned a little more about the file system. 

And some programs shows up in the Alacarte Menu Editor, even checked, but not in the Applications menu(?). After un checking them and then check the programs again; it showed up... 

Hi Ecthelion
I did not think about your solution; that would work. But arnt there any commands to run in the terminal to move a folder from A to B?

Sorry for my poor English!

---

### Post by CatKiller on 2006-11-05
> **Ecthelion said:**
> I don't really agree...
I think it's great to compile packages from source etc... It's something that is easily done in Ubuntu (I think that) and I find it very Linux- or even Ubuntu alike.

It's just that no-one expects an average user to do it that there aren't links for everything. And for someone who likes to install everything to see what it is, it's not a problem to make a link yourself...

... And that still is a lot Ubuntu-alike (or that's my opinion, but I know I would never have tried stuff like that if I still were on windows...)

My statement was poorly-worded too. I wasn't saying that compiling from source isn't very Linux, because obviously that would be untrue. Just that by avoiding the newbie-friendly solutions that Ubuntu provides is not the way for a newbie to accurately guage the Ubuntu experience. And installing a few programs - whether as binary packages, or compiling from source - on one platform is a vanishingly tiny aspect of the "Linux experience" if such a thing could be said to exist with the vast array of different distributions and platforms and the like. "I don't get icons on a menu" is a completely meaningless statement when considering a hardware router, for example, but that is still a machine running Linux.

Actually, I'm not convinced that this is any more clear than the last effort, but my dinner's ready :)

---

### Post by Oki on 2006-11-05
Hi kylevan;
Thanks for your tip, but I have done my “homework” and seekd a lot after digital photo programs for Linux. I have a list of about 48 different programs(meny of them can be found in synaptic), and have tried a lot of them, like F-spot and so on(F-spot is btw to slow showing RAW files, so no good I am afraid for that kind of work). Perhaps I should make a post when finishing trying them, and spare others coming from Windows the job(?). On thing is for sure; digital cameraproducers like Canon, Nikon and so on dont make programs for linux:-(

I always try to find the programs in Synaptic first, but when they are not there I have no choice. Thanks for the link, I shall read it. 


Hi again CatKiller.
As I wrote in the last post I am always trying Synaptic first, cus that is much easier for me. And then I can find the program later if I want to remove it. But; not all programs can bee found there, and if you need the program(I am looking for a image viewer that can show RAW files fast), then the manually part is the only solution. 

And, as I said in the last post; even though you find the program via Synaptic, and install it from there, it isn't always it appears in the Applications Menu. In fact; that have happened to me some times(and I have just started using Ubunut!!).

And programs showing up in the Alacarte Menu Editor – and checked, but not in the Application menu; that makes it even more strange – at last for me. 


So; no commands to run in the terminal to move a folder?

---

### Post by CatKiller on 2006-11-05
Sometimes when a program doesn't put an entry in the menu, it's because the program is designed to be run from the command line, or because it has no GUI of its own like Wine. Sometimes its because the developers have chosen not to have a menu entry, or because they've forgotten it. Sometimes the menu needs to be refreshed before they show up - like your ones that show up as ticked in Alacarte but not in the menu. Logging out and logging back in will fix this, as will using the command **killall gnome-panel**.

The thing to remember about the RAW "format" is that it is both proprietary and poorly-documented. Open source developers can persevere heroically if either of these are not true, with rapid and pleasing results, but since RAW has both those developers have struggled. Which is why such programs don't show up that often in the repositories.

You can move a folder with Nautilus. Or you can use the command **mv *folder1* *folder2***. The problem comes if a file elsewhere is expecting a file to be in *folder1* rather than *folder2*, which is why (I think) Ecthelion suggested the uninstall/reinstall procedure.

---

### Post by Kerry Lange on 2006-11-05
Hi there:

I'm a complete Linux / Ubuntu Newbie and I'm interested in Lightroom as well.  However, I've got the tarball but haven't got a clue what to do with it.  Can anyone point me to some docs on installing programs that aren't listed in Synaptic?

---

### Post by CatKiller on 2006-11-05
> **Kerry Lange said:**
>  Can anyone point me to some docs on installing programs that aren't listed in Synaptic?

You mean like [this one]("http://www.ubuntuforums.org/showthread.php?t=232059")? Or [this one]("http://www.ubuntuforums.org/showpost.php?p=1719134&postcount=11")?

---

### Post by Oki on 2006-11-05
Hi Kerry. kylevan was kind to post this link above [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/), regarding how to install “everything under Ubuntu”.

I just downloaded the file to the Desktop, double clicked it to unpack it to the desktop. This gave me a new folder called LightZone, inside it there is a file called lighzone witch I clicked to start the program. 


Thanks for your good explanation Catkiller, it is appreciated! I do want to learn how to use Ubunut Linux, and to do so I need to learn how things work. Belive me, it can be frustration for a newbie coming from that other OS. 

When it comes to RAW files; yes, there is less programs under Linux, and I do understand why. I hope some day there will be a open format for RAW. But I have found the programs for my needs here, so I am happy! Just wanted to try to find the best. 

I am a newbie, but I dont think I have installed anything – only unpacked the file to the desktop(?). In other words; there is no installer inside the package. 
I tried to move it with Nautilus, but got an error. And then I tried to download the file(again) to the Opt folder(where I belive “other” programs belong), but I got an error telling me that I have no write access. Then I tired to unpack it to my Opt folder, but error again. Guess I am missing the sudo part. 

It do no harm on the desktop, but I wanted to move it to the Opt directory and put an entry in the menu for it. Dont like icons on the Desktop. Perhaps I should leave it alone...

---

### Post by Kerry Lange on 2006-11-05
Hah... Yes...and no.  Those posts contain lots of links to installing info.  I'd looked at those a while ago and couldn't find a way to get LightZone installed or working.

There is no ".bin," ".deb," or other install-related file I could find.  The program is primarily Java-based and I was just reading that it's for x86-based Linux systems.  There is a "Lightroom" file in the extracted folder  whose properties tell me it's a shell script but when I try running it, nothing happens.

Could this program simply run from the extracted folder and is the reason it's not because I'm running the 64-bit (generic) kernel?

Here's a link to the LightZone page if anyone's interested:

[http://sonic.net.nyud.net:8080/~rat/lightcraft]("http://sonic.net.nyud.net:8080/%7Erat/lightcraft")

---

### Post by Kerry Lange on 2006-11-05
Oki:

I guess my problem *must* be the fact LightZone runs on x86 architecture but not AMD 64 bit.

---

### Post by Kerry Lange on 2006-11-05
> **CatKiller said:**
> You mean like [this one]("http://www.ubuntuforums.org/showthread.php?t=232059")? Or [this one]("http://www.ubuntuforums.org/showpost.php?p=1719134&postcount=11")?

Hah... Yes...and no. Those posts contain lots of links to installing info. I'd looked at those a while ago and couldn't find a way to get LightZone installed or working.

There is no ".bin," ".deb," or other install-related file I could find. The program is primarily Java-based and I was just reading that it's for x86-based Linux systems. There is a "Lightroom" file in the extracted folder whose properties tell me it's a shell script but when I try running it, nothing happens.

Could this program simply run from the extracted folder and is the reason it's not because I'm running the 64-bit (generic) kernel?

Here's a link to the LightZone page if anyone's interested:

[http://sonic.net.nyud.net:8080/~rat/lightcraft](http://sonic.net.nyud.net:8080/~rat/lightcraft)

---

### Post by CatKiller on 2006-11-05
> **Oki said:**
> I tried to move it with Nautilus, but got an error. And then I tried to download the file(again) to the Opt folder(where I belive “other” programs belong), but I got an error telling me that I have no write access. Then I tired to unpack it to my Opt folder, but error again. Guess I am missing the sudo part. 

It do no harm on the desktop, but I wanted to move it to the Opt directory and put an entry in the menu for it. Dont like icons on the Desktop. Perhaps I should leave it alone...

If you were trying to move it with Nautilus to a place you're not allowed to write to, you would get an error. You're right that **sudo mv** or **sudo cp** is more likely to work. You can **gksudo nautilus** to open a Nautilus window as root for drag-n-drop action with root permissions. You should be careful and use it sparingly, obviously.

You can make a menu entry for things easily enough in Alacarte, from the File menu.

---

### Post by CatKiller on 2006-11-05
> **Kerry Lange said:**
> I guess my problem *must* be the fact LightZone runs on x86 architecture but not AMD 64 bit.

AMD64 **should** run x86 code OK - that's the reason AMD's 64-bit processor took off quicker than Intel's. But the Requirements section says "You must use a Sun Java JRE." This **could** be your problem, although I've never used this LightZone myself.

---

### Post by Kerry Lange on 2006-11-05
> **CatKiller said:**
> AMD64 **should** run x86 code OK - that's the reason AMD's 64-bit processor took off quicker than Intel's. But the Requirements section says "You must use a Sun Java JRE." This **could** be your problem, although I've never used this LightZone myself.

That's what I thought when I first read that bit about being for x86 architecture.  Regarding the JRE, it comes with the bigger tarball, which is what I downloaded.  I assume if you get the tarball with the JRE included, it should run automatically.

Or, do I need to first install the JRE?

---

### Post by CatKiller on 2006-11-05
> **Kerry Lange said:**
> That's what I thought when I first read that bit about being for x86 architecture.  Regarding the JRE, it comes with the bigger tarball, which is what I downloaded.  I assume if you get the tarball with the JRE included, it should run automatically.

Or, do I need to first install the JRE?

Maybe you could try installing the JRE first, through Synaptic or whatever (there are posts on how to install Sun's Java, but I haven't read them) in case there is a difference between the AMD64 version of that, and the version in the tarball. That's entirely speculation on my part, though.

Others have reported that there's quite a lot of software that currently doesn't work that well with the 64-bit version of Ubuntu, and takes some tweaking to get working at all, and hence recommend people who are new to Linux install the 32-bit version even if they have a 64-bit processor. You might want to consider that if you haven't spent much time configuring your existing install. Just a thought.

---

### Post by Kerry Lange on 2006-11-06
You're conjecture was on the money.  I re-installed Ubuntu but this time the 32-bit version and Lightzone works fine.

---

### Post by CatKiller on 2006-11-06
Glad it's working for you. Hopefully as more people get 64-bit processors, more software will work properly on them with fewer problems. The price you pay for cutting-edge, I guess.

---

