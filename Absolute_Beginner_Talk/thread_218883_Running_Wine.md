---
title: "Running Wine"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by James_N on 2006-07-19
Hi

Sorry for creating a few threads but theres a few things im trying to get sorted.

I followed this guide and installed wine sucessfully: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Now how do i run it? do i just try and install a windows game and it runs automatically or what?

---

### Post by diepruis on 2006-07-19
Have a look at some wine-howto's on the forums, they should tell you what you need to know. If you want to run a windows application, you should invoke "wine pathtoapp". To install a windows game you should probably invoke "wine pathtoinstaller". Have a look at above mentioned howtos for more info.

---

### Post by James_N on 2006-07-19
doh! missed that.

Many thanks :)

---

### Post by Alien260 on 2006-07-19
> **diepruis said:**
> Have a look at some wine-howto's on the forums, they should tell you what you need to know. If you want to run a windows application, you should invoke "wine pathtoapp". To install a windows game you should probably invoke "wine pathtoinstaller". Have a look at above mentioned howtos for more info.

i m looking at wine as well and i read the Wine HowTo but still dont understand what i m suppost to do. 

any help? thanks (i installed wine using Synaptic)

---

### Post by 3rdalbum on 2006-07-19
> **Alien260 said:**
> i m looking at wine as well and i read the Wine HowTo but still dont understand what i m suppost to do. 

any help? thanks (i installed wine using Synaptic)

The version of Wine in the Ubuntu repositories tends to be a bit older. If you want best results, add the following to your sources.list:

```
deb http://wine.budgetdedicated.com/apt dapper main
```

Then when the file is saved, do a sudo apt-get update, and install the new Wine.

Running Wine is pretty easy. Go into a terminal and type:

```
wine "
```

Open a file browser and find the .exe file you want to run. Drag it to the terminal window. Switch back to the terminal window and delete the extra space, close the quotes, and hit Enter.

Presto!

If Wine complains about missing DLL files, find the particular file on your Windows partition and middle-drag it to ~/.wine/drive_c/windows/system. When you release the middle mouse button, choose "Link Here".

If you still have problems, consult the wine documentation for the command-line options or [www.frankscorner.org](www.frankscorner.org)

---

### Post by Dazza on 2006-07-19
Just a quick Q, I have Media Player 11 I want to install via Wine, now exaclty what do I type when the Wmp11 file is in my winetools sys directory?


/home/dazza/winetools/sys/Wmp11.exe 

Thanks.

---

### Post by diepruis on 2006-07-19
> **Dazza said:**
> Just a quick Q, I have Media Player 11 I want to install via Wine....

Why do you want to install MP? If there's a native linux app that will work use that instead. Post what you want to do and I'll point you in the right direction.

[QUOTE=Alien260]i m looking at wine as well and i read the Wine HowTo but still dont understand what i m suppost to do.[/QUOTE]

What are you having trouble with, specifically? If its more than one problem, post a list.

---

### Post by Alien260 on 2006-07-20
i installed wine but it gives me some problems when i need to run it. 
i dont understand what the the problem is?? 

this is the message i get.

alien@alien:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
alien@alien:~$ wine PROGRAM
wine: creating configuration directory '/home/alien/.wine'...
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
wine: '/home/alien/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found


thanks

---

### Post by aeto on 2006-07-20
like the terminal states, "Usage: wine PROGRAM". And PROGRAM is the name of the file u want to run with wine.

Example:

U downloaded a windows application/setup named "this isnt real.exe" to /home/alien/Desktop. So u would enter the following in the terminal:

wine "/home/alien/Desktop/this isnt real.exe"

---

