---
title: "Pioneer DVD RW 111-D Won't Burn"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by yochaigal on 2007-02-20
Hello. I have a Pioneer DVD RW 111-D. It works fine in windows (burning, reading, etc).
but in ubuntu, in only reads (dvds and cds).  when i try to burn using any program (banshee, nerolinux, command)  it just gives me toasters.
what do i need to do? i have the most recent firmware....

note: when i check cdrecorder -scanbus, the drive does not show up. somehow, my hard drive does though.

---

### Post by tbroderick on 2007-02-20
Where is your drive located? /dev/hdc? When you try cdrecord do;
```
sudo cdrecord dev=/dev/hdc
```

Edit: try,
```
sudo cdrecord --devices
```

I'm not sure if cdreocrd has the --devices switch though. I'm on Debian and they use a fork of cdrecord called wodim.

---

### Post by darrenn on 2007-02-20
I own this recorder and it works perfect for burning and playing dvd's. Im not sure what your problem is but it is absolutely not the recorder. 

I haven't updated my firmware because i didn't see the need to.

---

### Post by yochaigal on 2007-02-20
what code did you input?  or what software do you use?  I can't seem to get either to work.
by the way, the second code suggested above didn't work---i think that it's specific to the debian they mentioned.

thanks!

---

