---
title: "WINE or Cedega?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-02-17
I have installed the newest version of WINE, but it doesnt seem to install hardly any of my windows apps. The ones that it installs dont appear to work at all. I am wondering if Cedega would be worth the subscription fee, or if I will be paying for the same things? I  would rather use WINE if it would work. It may just be my lack of experience with WINE that is causing the problem. Any advice on the use of WINE or Cedega?

---

### Post by Velotix on 2007-02-17
A lot of Windows programs were written assuming that the person using them had admin access to their computer. Because that's never the case in Linux by default, a lot of programs that should work fine die a horrible death because of poor coding.

To get them to work, you'll have to use *sudo*, which you probably have some experience using. Just remember: **this is potentially very dangerous so be absolutely sure the program can't do anything that could wreck your computer before continuing**.

Or, to put it in a less intimidating way: don't use any lame Windows program that'll let you save over your Linux system files without you telling it to explicitly. :P

Example: There's a Windows program I like called UnFREEz that allows me to make animated GIFs. It is therefore essentially harmless. Yet bizarrely, I have to have admin access to the computer to use this 11K .exe file. That's just stupid coding. :/

You shouldn't have to use sudo for a **.gif creator**.

---

### Post by HgBoy on 2007-02-17
I only plan on running a handful of my windows games, and possibly autocad. I am familiar with the sudo command, but have only been using linux for 4-5 days. I have had to jump in with both feet and learn to compile source (horrible driver issues), and use other fairly advanced commands. How exactly would I apply the sudo command when using wine? (my extent of knowledge on WINE is to right-click and select "run in wine".) I'm running an amd64 processor and am not sure if I have taken care of the little loophole required for this.

---

### Post by tbroderick on 2007-02-17
> **HgBoy said:**
> I only plan on running a handful of my windows games, and possibly autocad. I am familiar with the sudo command, but have only been using linux for 4-5 days. I have had to jump in with both feet and learn to compile source (horrible driver issues), and use other fairly advanced commands. How exactly would I apply the sudo command when using wine? (my extent of knowledge on WINE is to right-click and select "run in wine".) I'm running an amd64 processor and am not sure if I have taken care of the little loophole required for this.

What games do you plan to run? You should check the wine db and the unofficial transgaming wiki to see which one can run your games or apps.

[wine db]("appdb.winehq.org")
[unofficial trangaming wiki]("http://cedegawiki.sweetleafstudios.com/wiki/Main_Page")

You shouldn't need to use sudo to use wine in fact  I have never run wine as sudo. You should use it from the terminal. The first thing you should do is open a terminal, ALT-F2 and type gnome-terminal, and run winecfg. It should create your wine folder, basically a dummy windows folder in your /home/username, and a configuration GUI will appear. To install or run a game, type in the terminal, wine /path/to/game.exe. It should either install or run if it's supported. Then it's better to run the game from the terminal. wine ~/.wine/drive_c/Program\ Files/GameName/game.exe. With some games, you might have to cd to the folder and run wine game.exe instead.

---

### Post by dixonstalbert on 2007-02-17
Crossover by codewevers.com  is the paid version of wine.

They offer a trial version and a large website which tells you what people have got to run and what not. Here is the link:


[http://www.codeweavers.com/compatibility/]("http://www.codeweavers.com/compatibility/")


I looked at autocad and it is a total no go. I cannot see it running satisfactorily in vmware either because it would be so slow under virtural graphics hardware. Looks like you will have to stay with XP for now...


I have been using Quickbooks, Taxexpress, and Microsoft Office using Crossover and have not had any problems except when they are interacting with IE5.5

---

### Post by Velotix on 2007-02-17
This is more information than you probably want, but I think it'll help you understand exactly what Wine is and how it works:

When it comes to programming, you have a lot of choices as to how you get your program to talk to the hardware to tell it what to do. Often, when you compile a program, the compiler adds in these instructions. You can, of course, add them in yourself, or create your own interfaces if you feel really adventurous.

For most people though, they're quite happy to just use a standard interface for getting their code to talk to hardware properly. They're called APIs, or Application Programming Interfaces. Linux uses the POSIX interface to perform procedure calls to the kernel and OS, so naturally any program running on Linux has to do things the POSIX way. Alternatively for games and anything graphically intensive, Linux can use OpenGL, which is designed to allow programs to just jump right to talking to the hardware directly, which saves a lot of processing time and speeds up graphics rendering considerably, making games possible. Try running games without OpenGL acceleration and you'll see what I mean.

Windows, whilst it can use OpenGL, it can't use POSIX by default. Instead, as Microsoft are so keen to do, they have created their own APIs: the Win32 programming environment for 32-bit processors, and DirectX for speedy graphics rendering, as well as a number of features for improved sound quality. (I imagine Windows Vista uses a new Win64 API because it's 64-bit, so that's a headache to come for us all. ^^)

This brings us to Wine, and indeed Cedega: both are charged with converting Win32 and DirectX procedure calls into POSIX and OpenGL respectively - Wine isn't so much an emulator as a **translator** to make Linux understand Windows programs. This translation naturally makes instructions take longer to get processed, so the end result is the same, but slower, which is why people will often comment that programs run worse in Linux than natively in Windows.

Now to your question (finally :P). To run something under Wine is quite simple: type this into the command line:

```
wine [filename]
```

Or if the program needs admin access to work correctly:

```
sudo wine [filename]
```

Wine accepts both Linux file paths and emulated Windows file paths (yes, you guessed it, they're converted into Linux file paths by Wine). If you use a Windows filename, make sure to put quote marks (") around it otherwise Wine will throw a hissy fit - that's because Windows filenames often have spaces in them and Linux ones usually don't (unless you're a risk taker). You can put quote marks around the Linux filenames too: it'll do the same job.

Examples of acceptable Wine commands:

```
**Windows-style file paths:**
sudo wine "C:\Program Files\UnFREEz\UnFREEz.exe"

**Regular Linux-style file paths:**
wine /home/user/cheese/biscuits.exe

**Linux-style file paths for files with spaces in their name:**
wine "/etc/X11/superfluous exe file.exe"
```


Using sudo to run Wine as root is never recommended, as has been said, but is sometimes necessary as I explained before. Another thing to remember is that whilst Wine is supplied with a set of useful .dll files, you may need extras to run certain programs properly, but I believe technically in order to use these .dll files you must have a valid Windows license. If you do, there's no worry. If you don't, beware.

---

### Post by HgBoy on 2007-02-17
Ok, so if I want to run a dual boot system, is it possible to install XP onto my edgy only machine without it interfering with my current setup? I REALLY don't want to have to go through the whole driver nightmare again. I also dont have too much experience with partitioning hard drives. I let edgy do that for me :P

---

### Post by Velotix on 2007-02-17
Unfortunately, Windows was designed to run as a stand-alone operating system, so when it installs, it installs its own bootloader, overwriting any existing one like the one Ubuntu uses, GRUB, making it impossible to access your Ubuntu OS even though it's still there.

Also, you will need to partition your hard drive to make room for Windows, because Linux uses file systems that Windows can't read without extra software (though Linux can read Microsoft file systems just fine). As you can imagine, if Windows finds a file system it can't read, it'll assume it's corrupt and format it, destroying your data.

Ubuntu's installer is much more considerate, hence why it's recommended that if you want to have a dual-boot system, install Windows, THEN Linux. Doing it the other way round usually requires a lot of extra patience and probably an extra hard-drive. :/

I'm in the same boat as you, and I've decided to go with getting a new hard drive to stick Windows on so it doesn't crush my Ubuntu installation underfoot. The problem is installing Windows second requires letting it install its own bootloader and then overwriting it again with GRUB (you'll need the LiveCD and someone with more experience than me, because I've not done this yet).

If you're asking this because of what I said about reduced performance, for most applications in Wine the difference in performance is usually unnoticeable because computers are so fast these days. If you do go through with putting Windows on your computer, I recommend backing EVERYTHING UP first, just in case. Hopefully your Linux install is still small enough to get all of it onto a DVD because it's so new, and if you can, then you can always stick it back on your HD later.

---

