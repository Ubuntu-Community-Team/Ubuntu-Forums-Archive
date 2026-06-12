---
title: "Installing an exe file"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Nezing on 2007-06-22
As we all know,an exe file to linux,is like trying to digest the da vinci code :)
I have Wine installed.I have also read somewhere that if you type the name of the exe file in Terminal (after you have installed Wine),the file can be installed.Or am I being stupid.
No sarcasm please lads,as I'm still learning.

This is what I read somewhere:

Once Wine is installed, you can run programs in Wine by using the terminal (Applications > Accessories > Terminal). Then if you want to try to install/run a program under Wine do this:

1. Download an EXE file.

2. Navigate to the directory of the EXE file using the cd command in the terminal.

3. Type in "wine EXENAME.exe" and it will then run the install.

I have tried this.For me,it does zip.

---

### Post by jkblacker on 2007-06-22
I'm not sure if it can install exactly, but I know it works for applications already installed on a windows partition - for example, I can run Unreal Tournament via wine from my windows hard drive by running
 ```
wine /media/harddrivepath/UnrealTournament/System/UnrealTournament.exe
```

---

### Post by Happy_Man on 2007-06-22
What application are you trying to install? Generally, there's a Linux alternative.

---

### Post by Nezing on 2007-06-22
MediaCoder 0.5.1-r9.exe

I do not have XP installed (dual-boot), as I want to leave the past alone. :)

---

### Post by LaRoza on 2007-06-22
I noticed there is a space in that name, if the executable's has a space, put it in quotes otherwise Linux will not find it.

```

wine "MediaCoder 0.5.1-r9.exe"

```

---

### Post by atlfalcons866 on 2007-06-22
try this
[http://mediacoder.sourceforge.net/wiki/index.php/MediaCoder_on_Linux](http://mediacoder.sourceforge.net/wiki/index.php/MediaCoder_on_Linux)

---

### Post by Alien260 on 2007-09-09
So just that  i can understand you cant install a .exe on linux u can only point to a pre-windows installed .exe on the windows partition and run it from there. 

If this is right, does this mean that if i wanted to install a windows games (without having a windows partition on my computer ) i couldn't do it?

Thanks

---

### Post by shae on 2007-09-09
You do not have to have windows installed to use wine.  If you would like to install a game, simply point wine to the installation exe.  For example:
```
wine /media/cdrom0/install.exe
```

---

### Post by Alien260 on 2007-09-09
ok, here comes the stupid question but i have an .exe on my desktop and well i point wine to it but it just says thats it cant fine "c:\\windows\\system32\\Second.exe"

what do i need to do to install it or anything that is a exe?

Thanks

---

### Post by [Alsharifi] on 2007-09-09
> **LaRoza said:**
> I noticed there is a space in that name, if the executable's has a space, put it in quotes otherwise Linux will not find it.

```

wine "MediaCoder 0.5.1-r9.exe"

```

yes there shouldnt be any spaces 


i always ran wine like this.

```
wine ~/path/to/file/Program.exe
```

---

