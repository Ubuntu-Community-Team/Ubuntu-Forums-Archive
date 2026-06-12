---
title: "mupen 64 crashes computer"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-12-28
I just installed Mupen, installed fine. I downloaded the Zelda 64 ROM, and ran it, everythings fine, game loads and runs smoothly at about 20 fps, then about 30 seconds in, it just bugs out and freezes up, locks up my computer and I have to shut down.

what gives here? much obliged for any wisdom

Kev

---

### Post by SOULRiDER on 2007-12-28
It may be issues with your video card, what card do you ahve and what drivers are you using?

---

### Post by KevNice on 2007-12-28
Its just a standard Dell video card, by Intel Graphics. The drivers on Mupen are set at default, are there specific ones I should use?

---

### Post by SOULRiDER on 2007-12-28
Those drivers have acceleration AFAIK so theres no problem there. try googling around and see if someone has issues like yours, or try another emulator.

---

### Post by KevNice on 2007-12-28
Im trying to setup a different emulator, called Project 64 I believe, but the file I have is an .exe file, when I clicked on it I got the following message:

"No application suitable for automatic installation is available for handling this kind of file."

I realize this is a super-noob question, but how do I install it?

---

### Post by SOULRiDER on 2007-12-28
Is ti for windows or is it for Linux? You are aware you won't be able to use windows applications without something like Wine right?

---

### Post by KevNice on 2007-12-28
well i found it on the forums here so I assumed its linux, but I think they mentioned wine as well so maybe not then.

 Is it like crossover office? Simply type "apt-get install wine" and then install it through that?

---

### Post by SOULRiDER on 2007-12-28
> **KevNice said:**
> well i found it on the forums here so I assumed its linux, but I think they mentioned wine as well so maybe not then.

 Is it like crossover office? Simply type "apt-get install wine" and then install it through that?

Yup
```
sudo aptitude install wine
```
and then to run an exe
```
 wine <path to .exe>
```

---

### Post by KevNice on 2007-12-29
ok, I gave it a shot but when I try to run the file I get this output:

```
~/Desktop$ wine setup Project 64 1.6.exe
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found
```


filename is <setup Project 64 1.6.exe>

should I reinstall wine then?

---

### Post by doorknob60 on 2007-12-29
Try this:
```
wine ./Project\ 64\ 1.6.exe
```
that should work hopefully.

---

### Post by KevNice on 2007-12-29
thanks doorknob, that command worked and Project64 is now installed.

however, now when I run Project64 and open the ROM, the program vanishes and nothing happens...

---

### Post by SOULRiDER on 2007-12-29
It's probably crashing. Does the wine console show any errors? If youre opening it form your applications menu go to:
```
~/.wine/drive_c/Program Files/....
``` (basically where it is installed under the wine folder) and run the exe just like you did with the isntaller. That will show any errors you can get.

---

### Post by KevNice on 2007-12-29
k here we go, this is the output I got:

```
laptop:~/.wine/drive_c/Program Files$ ./Project64.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x34f340,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1301e8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1301e8) : stub
fixme:win:EnumDisplayDevicesW ((null),0,0x78b70000,0x00000000), stub!
err:ntdll:RtlpWaitForCriticalSection section 0x7e5dc860 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 001c, blocked by 0024, retrying (60 sec)
wine: Critical section 7e5dc860 wait failed at address 0x7bc39110 (thread 001c), starting debugger...
Unhandled exception: wait failed on critical section 0x7e5dc860 X11DRV_CritSection
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39110
Process of pid=001b has terminated
No process loaded, cannot execute 'echo Modules:'
kevin@kevin-laptop:~/.wine/drive_c/Program Files$ Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
No process loaded, cannot execute 'detach'



```

and it just stops there, I had to close out terminal because I couldnt exit

---

### Post by SOULRiDER on 2007-12-29
Sorry, i really have no idea whats wrong :(

---

### Post by KevNice on 2007-12-30
no worries soulrider, thanks for your help up til now!


anyone else have an idea?

---

