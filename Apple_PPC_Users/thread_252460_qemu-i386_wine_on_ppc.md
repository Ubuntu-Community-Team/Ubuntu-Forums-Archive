---
title: "qemu-i386 wine on ppc"
date: 2006-09-06
forum: Apple PPC Users
---

### Post by maddocks on 2006-09-06
I have a ppc ibook g3 running ubuntu dapper. I would like to try running wine via qemu-i386. I know many people have done it but I cant find a how-to anywhere. The qemu documentation mentions a wine download available on the qemu homepage but it doesnt exist I dont know if it ever did. Here is what I have tried

After getting really tired of downloading/extracting all kinds of x86 binarys and debs, I copied the whole /usr , /lib /bin directories and sub-driectories from my x86 ubuntu dapper install. I copied them over the /usr/local/gnemul/qemu-i386/ directory. Now in theory I have all the wine binary's and libs plus all the standard x86 libs and binarys that my x86 laptop has. So then how do I start it? Well I downloaded and installed qemu's gnemul and tests packages. For the most part gnemul have an x86 glibc and also create the /usr/local/gnemul/qemu-i386 directory and populates it with /usr /etc and such. The test package installs a couple of more lib's and some x86 binarys like the "ls" command.

So now we test qemu-i386 ability at runnen a simple x86 app on a ppc processor. So I type 
"qemu-i386 /usr/local/gnemul/qemu-i386/ls" wich runs the x86 version of the ls command.(note the test package installs the ls binary to that location) And it WORKS!!!
So now lets try loading wine the same way
"qemu-i386 /usr/local/gnemul/qemu-i386/usr/bin/wine" and get missing ld-linux.so.2
Well qemu-i386 has a switch "L" Im not entirely sure what this switch does but I believe it points to the x86 libs that an app needs to run (default being /usr/local/gnemul/qemu-i386/) which is where the "ls" binary resides. So I tried
"qemu-i386 -L /usr/local/gnemul/qemu-i386/usr/lib /usr/local/gnemul/qemu-i386"
Wich resulted with this error "qemu: uncaught target signal 11 (segmentation fault)"
Obviously after the -L I added the path to the wine libs then added the path to the wine executable. So its time to write a shell script to cover much more then these attempts.After much research alot of guessing I came up with this wine start script;

"declare -x WINEDLLPATH="/usr/local/gnemul/qemu-i386/usr/lib/wine"
declare -x
LD_LIBRARY_PATH="/usr/local/gnemul/qemu-i386/usr/lib:/usr/local/gnemul/qemu-i386/usr/X11R6/lib"
qemu-i386 -L /usr/local/gnemul/qemu-i386 /usr/local/gnemul/qemu-i386/usr/bin/wineserver
qemu-i386 -L /usr/local/gnemul/qemu-i386 /usr/local/gnemul/qemu-i386/usr/bin/wine-pthread 
/home/student/.wine/win/drive_c/windows/notepad.exe"

Here are the errors I get on each command the first command declare with the WINEDLLPATH goes thru fine and then the declare -x shows WINEDLLPATH=blah blah correctly. the third line LD_LIBRARY_PATH also works fine no errors. the next qemu-i386 for wineserver gives the error
that ld-linux.so.2 is missing. So I change the command to
"qemu-i386 -L /usr/local/gnemul/qemu-i386/usr/lib /usr/local/gnemul/qemu-i386/usr/bin/wineserver"
wich results in the all to familiar error "qemu: uncaught target signal 11 (segmentation fault)".
the 5th line also complains about missing ld-linux.so.2 and if I add the path to that file after the -L switch I get the uncaught target signal (segmentation fault) again. So I'm assuming my problems are caused by one of three things
1. I'm not using the -L switch correctly 
2. My qemu (was compiled from source) has some errors in it
3. the x86 libs and binarys from my laptop are incompatable (considering all the executable from the test package works but non of the ones from my x86 laptop dont might be a clue.
4. Im retarded and have gone about doing this all the wrong way (which is usually the case:)

This is my first forum post, Im sorry for the bad grammar and long windedness of it all but I wanted you to know exactly where I am and where I came from. Thank you again. A how-to or some tips and tricks anything would be great. I decided to use LD_LIBRARY_PATH and WINEDLLPATH commands on my own after searching for commands to set libs paths, so I might be using them inncorectly I have a hard time following man pages some times.

---

