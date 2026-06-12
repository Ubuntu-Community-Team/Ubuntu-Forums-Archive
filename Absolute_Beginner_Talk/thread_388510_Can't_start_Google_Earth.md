---
title: "Can't start Google Earth"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-19
Has anyone had trouble getting Google Earth to start and figured out how to fix it? I can't get past the splash screen. If you can help, I sure would appreciate it.
kh

---

### Post by taurus on 2007-03-19
To run Google Earth, you first need to install a driver for your graphic card, 3D.  Have you installed a driver for your graphic card?  Otherwise, run it from a terminal to see what the error message is.

---

### Post by kittyhawk63 on 2007-03-19
> **taurus said:**
> To run Google Earth, you first need to install a driver for your graphic card, 3D.  Have you installed a driver for your graphic card?  Otherwise, run it from a terminal to see what the error message is.

Hello Taurus,
Yes, I have a driver downloaded for my ATI Radeon 9200SE.
What is the run command for Terminal?

---

### Post by taurus on 2007-03-19
For KDE, it's KMenu > System > Konsole.  Then, type the name of the program to run it, assuming it's in your path.

```
googleearth
```

---

### Post by kittyhawk63 on 2007-03-19
> **taurus said:**
> For KDE, it's KMenu > System > Konsole.  Then, type the name of the program to run it, assuming it's in your path.
```
googleearth
```

kittyhawk63@kittyhawk63:~$ googleearth
bash: googleearth: command not found
kittyhawk63@kittyhawk63:~$

---

### Post by taurus on 2007-03-19
Do you remember where you installed Google Earth?

```
find ~ -name googleearth -print
```

---

### Post by kittyhawk63 on 2007-03-19
> **taurus said:**
> Do you remember where you installed Google Earth?
```
find ~ -name googleearth -print
```


Automatix2 installed it. I can find it listed in K Menu -> Internet->3D Planet Viewer [Google Earth]. However, once I click it, it only goes to the splash screen and freezes.

kittyhawk63@kittyhawk63:~$ find ~ -name googleearth -print
/home/kittyhawk63/google-earth/googleearth
/home/kittyhawk63/googleearth
kittyhawk63@kittyhawk63:~$

---

### Post by der_vegi on 2007-03-19
same here. can't get past the splash screen either. the splash is shown until i kill the process. no errors in the terminal.

maybe an error in google earth?

btw: i'm running feisty daily build amd64

---

### Post by ounn on 2007-03-19
I have exactly the same problem and the same graphic card :-k

I have the drivers installed. At least i suppose...

```

nuno@nuno-desktop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8

```

When i run googleearth from the command line i get no errors but the application never starts, i only can see the splash screen.


ounn

---

### Post by taurus on 2007-03-19
```
cd ~/google-earth
./googleearth
```

---

### Post by kittyhawk63 on 2007-03-19
> **taurus said:**
> ```
cd ~/google-earth
./googleearth
```

Ran both commands, one and then the other. Still only the splash screen. Did you notice that two others were having the same problem? Maybe it is a Google Earth problem. What do you think, Taurus?

---

### Post by kittyhawk63 on 2007-03-19
[quote=ounn;2323287]I have exactly the same problem and the same graphic card :-k
[/code]When i run googleearth from the command line i get no errors but the application never starts, i only can see the splash screen.

Same problem here, Ounn. Maybe Taurus will be able to help out, Stay tuned.

---

### Post by der_vegi on 2007-03-19
ah. ```
./googleearth
``` doesn't give any output. but ```
./googleearth-bin
``` gives ```
./googleearth-bin 
./googleearth-bin: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: No such file or directory
```

installing libcrypto++5.2c2a doesn't do the trick...

---

### Post by kittyhawk63 on 2007-03-19
Taurus, did you see this?

kittyhawk63@kittyhawk63:~$ cd ~/google-earth
kittyhawk63@kittyhawk63:~/google-earth$ ./googleearth-bin
./googleearth-bin: error while loading shared libraries: libfreeimage.so.3: cannot open shared object file: No such file or directory
kittyhawk63@kittyhawk63:~/google-earth$

---

### Post by kittyhawk63 on 2007-03-19
> **der_vegi said:**
> ah. ```
./googleearth
``` doesn't give any output. but ```
./googleearth-bin
``` gives ```
./googleearth-bin 
./googleearth-bin: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: No such file or directory
```installing libcrypto++5.2c2a doesn't do the trick...

Note: Der_Vegi, you and I had different results. yours say so. o.9.8. Mine says so. 3...

---

### Post by kittyhawk63 on 2007-03-19
> **der_vegi said:**
> ah. ```
./googleearth
``` doesn't give any output. but ```
./googleearth-bin
``` gives ```
./googleearth-bin 
./googleearth-bin: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: No such file or directory
```installing libcrypto++5.2c2a doesn't do the trick...
Note: Der_Vegi, you and I had different results. yours say so. 0.9.8. Mine says so. 3...

Well, I keep reading to make sure that 3D is installed or activated. How can I tell if it is?

---

### Post by kittyhawk63 on 2007-03-19
> **taurus said:**
> ```
cd ~/google-earth
./googleearth
```


 Well, I keep reading to make sure that 3D is installed or activated. How can I tell if it is?

---

### Post by Thingymebob on 2007-03-21
It may be your ATI driver thats causing the problem type fglrxinfo in the terminal to see what version you have, Check this thread [http://ubuntuforums.org/showthread.php?t=196011&highlight=google+earth+amd64]("http://ubuntuforums.org/showthread.php?t=196011&highlight=google+earth+amd64") It appears that version 8.26.xx will work but anything newer is causing problems.

---

### Post by Thingymebob on 2007-03-21
It may be down to this from AMD site:
737-20868: Linux Distibutions with Modified XOrg X Servers May Not Be Compatible with the 3D Driver

    The information in this article applies to the following configuration(s):

        * XOrg 6.8.2
        * Linux

    Attempting to install the Driver on distributions that have updated certain 3D components outside of the stock XOrg 6.8.2 may result in the driver improperly initializing 3D applications.

    ATI Engineering has been advised of this issue and is investigating it. Any updates will be published when they become available.
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge")

---

### Post by kittyhawk63 on 2007-03-21
Thanks for the information Thingymebob.
kh

---

### Post by Thingymebob on 2007-05-12
So I have revisited this and finally got it running. heres how:
download libGL.so.1.2 from here [http://www.ground-impact.com/]("http://www.ground-impact.com/")
copy it to your googleearth install directory, for me this was /opt/google-earth
rename it to libGL.so.1
run googleearth

Don't be tempted to overwrite any existing versions of libGL.so.1, you could screw everything up.

It Runs, it a'int brilliant or fast but its going, I will play with a few different versions of liGL.so.1 and see what works best.

---

### Post by Toontwnca on 2007-05-12
Same problem here.
With me though it works fine if I don't use Beryl.

---

### Post by Angelbeast on 2007-05-21
> **Thingymebob said:**
> So I have revisited this and finally got it running. heres how:
download libGL.so.1.2 from here [http://www.ground-impact.com/]("http://www.ground-impact.com/")
copy it to your googleearth install directory, for me this was /opt/google-earth
rename it to libGL.so.1
run googleearth

Don't be tempted to overwrite any existing versions of libGL.so.1, you could screw everything up.

It Runs, it a'int brilliant or fast but its going, I will play with a few different versions of liGL.so.1 and see what works best.

i tried this and it does work now...but you're right it ain't fast *LOL* ... 

I get a message whenit starts up about runningin emulaton mode and to update my graphics drier. I do have an ati card. The radeon xpress 200 ... i downloaded the newest driver but i don't know how to install it...

---

### Post by teetee on 2007-05-24
Thanks. I got it working. Have you (Thingymebob or somebody else) discovered any ways to make it faster?

---

### Post by moshuptrail on 2007-05-24
It appears that the value for $LD_LIBRARY_PATH is not being set properly in the script.
It is only looking in the local (install) directory for libraries.

---

### Post by teetee on 2007-05-25
> **moshuptrail said:**
> It appears that the value for $LD_LIBRARY_PATH is not being set properly in the script.
It is only looking in the local (install) directory for libraries.

So, is there something to do about it?

---

### Post by kittyhawk63 on 2007-05-25
I got it to work and the speed is actually faster than it is in Windows XP. I used ENVY to install my ATI video driver. I downloaded the file suggested by Thingymebob and installed it into the folder suggested renaming it as suggested. It works great.
Thanks for all the great suggestions. :D
kh

---

### Post by speedygeo on 2007-05-27
The Automatix wiki write that Googleearth don't works on debian-based distro when we use an ATI graphics card!!!

---

### Post by scottfro on 2007-10-23
thanks, this worked for me!

---

