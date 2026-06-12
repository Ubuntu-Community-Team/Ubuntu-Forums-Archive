---
title: "Can't get Cinelerra to function.....Please help"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-26
There have been many threads on this subject and many sources of information on how to download/install Cinelerra. However, despite several attempts, using different methods, I still can't get the app. to function.

Here is my setup :-

System - Ubuntu 7.04
Video adapter- Geforce MX4000
(System is using nVidia accelerated 3D driver)
Processor-Amd athlon xp
Ram - 256Mb

When I click on the Cinelerra icon, all I get is a screen outline in the top left-hand corner of my display, which appears/disappears in a flash.

Any ideas anyone ?

---

### Post by throntax on 2007-05-27
from where did you install the program from? Not that i have any idea what the problem might be

(actually, maybe try removing the config directory in you home dir.
typing 
rm -rf .bcast
in your home dir will remove it in case there's a dodgy file in there somewhere. )

It's a shame, I really like cinelerra. Really complex but gotta love that!
 
the best version of cinelerra I have run is the current one from the community version cinellera site 
[http://cvs.cinelerra.org/](http://cvs.cinelerra.org/)
good general instructions there for adding which repository etc..
good luck!

---

### Post by linuxnooby on 2007-05-27
Quote :"the best version of cinelerra I have run is the current one from the community version cinellera site 
http://cvs.cinelerra.org/"

Been there, done that (didn't get the T-sshirt though) - Doesn't work for me, whichever processor I choose.

Ah well, I'll have to search for a different authoring package.

Thanks, anyway

---

### Post by throntax on 2007-05-28
The first version I used was about four years ago, had to compile it from source! 

Maybe you should try entering cinelerra from the command line to check for errors. So deleting ~/.bcast didn't help?

---

### Post by linuxnooby on 2007-05-28
Deleting as per your suggestion did not help. The message I get when typing cinelerra into the console is:-

Illegal instruction (core dumped)

---

### Post by throntax on 2007-05-29
I googled the error around and it looks like your problem is quite a common one with the ubuntu pakages. as per this link
 [http://www.kiberpipa.org/~gandalf/blog/?p=77](http://www.kiberpipa.org/~gandalf/blog/?p=77)
the best solution any one of them came up with was compiling the lot from source, which from experience is a complete nightmare of dependencies.

---

### Post by Limitlesschannels on 2007-05-29
EDIT:  i fixed the repos, originally it was the i686 architecture (hence the error further down) but it should work for at least linuxnobby now.  For others, make sure you have the appropriate  architecture; check cvs.cinelerra.org

Oh, yeah, remember this.  Cinelerra is a tough little bugger to get running.  I had to compile from source after spending a day or two gathering dependencies and working around some errors that i can't really remember.  Your best bet is just to keep trying, either that or dual boot ubuntu studio, err, if it has cinelerra's on it...

but i believe it might work out now from the repos.  Tack these onto your /etc/apt/sources.list:

```

deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/ ./
deb http://archive.ubuntustudio.org/ubuntustudio feisty main

```

then just apt-get install cinelerra.

hope that works out for you.

---

### Post by throntax on 2007-05-29
yeah Cinelerra isn't in ubuntu studio, I converted to it from AMD64 kubuntu a week or so ago. Cinelerra from the cvs site installed pretty easily into it though.

When I tried cinelerra from source, from memory the main problem i had was trying to configure ffmpeg properly. I used to use kino to convert from dv to quicktime, but discovered after a weeks frustration with getting quicktime export working in kino that cinelerra now just seems to support it!  However from reading the above link about the framerate achieved by compiling  yourself, I'm seriously considering it again, half out of masochism, half out of procrastination...

---

### Post by linuxnooby on 2007-05-29
Upon entering the ubuntustudio source into the sources list, I get the following error :-

W:GPG error: The following signature could not be verified because the public key is not available:NO_PUBKEY A361B38AB6A4EB33

Any suggestions ?

Thanks for the link which highlights the other error message, by the way.

---

### Post by kelvin spratt on 2007-05-29
i used cinelerra in fiesty its a nightmare to get installed i just kept on reinstalling then for some reason it worked. it works excellent in DAPPER.just add..deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
	deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./  Do the sudo bit make sure you paste in all the quotes reboot thats it

---

### Post by linuxnooby on 2007-05-29
Re Dapper. I entered the details you gave in sources, did sudo apt-get update and this is what came back :-

Failed to fetch [http://kiberpipa.org~gandalf/ubuntu/dapper/cinelerra/i686/./Release.gpg](http://kiberpipa.org~gandalf/ubuntu/dapper/cinelerra/i686/./Release.gpg)  Could not resolve ‘kiberpipa.org~gandalf’
Failed to fetch [http://kiberpipa.org~gandalf/ubuntu/dapper/cinelerra/i686/./en_GB.bz2](http://kiberpipa.org~gandalf/ubuntu/dapper/cinelerra/i686/./en_GB.bz2)  Could not resolve ‘kiberpipa.org~gandalf’
Failed to fetch [http://kiberpipa.org~gandalf/ubuntu/dapper/cinelerra/i686/./Packages.gz](http://kiberpipa.org~gandalf/ubuntu/dapper/cinelerra/i686/./Packages.gz)  Could not resolve ‘kiberpipa.org~gandalf’

????

---

### Post by kelvin spratt on 2007-05-29
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools[/url] ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/[/url] ./
this is the Two that I used 5 days ago sorry if i gave you wrong ones these worked with dapper for me also gives support for quicktime in Cinelerra as my vid cam writes to SD cards. i hope i got it right this time
these url did not com out right i hope this does  if they don't i'll mail them to you

---

### Post by kelvin spratt on 2007-05-29
Thats better thats the ones ive got pasted in synaptic and they worked for me

---

### Post by linuxnooby on 2007-05-29
Thanks Kevin. Yes, the update worked with the revised deb.s but when I did sudo apt-get install cinelerra, this is the error message that came back :-

The following packages have unmet dependencies.
  cinelerra: Depends: libguicast (= 1:2.0.0-1svn20060611.1) but 1:2.1.0-2svn2007424ubuntu3 is to be installed
             Depends: libquicktimehv (= 1:2.0.0-1svn20060611.1) but 1:2.1.0-2svn2007424ubuntu3 is to be installed
             Depends: libmpeg3hv (= 1:2.0.0-1svn20060611.1) but 1:2.1.0-2svn2007424ubuntu3 is to be installed
E: Broken packages

This is going from bad to worse. Seems like I'll have to look for another authoring package, unless of course, the above error makes any sense to you and a solution is possible.

---

### Post by kelvin spratt on 2007-05-29
it just loaded from those files using Dapper not Fiesty You can use Pc Linux Cinelerra is in the Repository 
works sort of strange you have to sign in as root to use Cinelerra and it does not support Quicktime but supports mp4 but for me was no good as i'd be double converting and i've had the same probs in windows, Pure Dyne supports Quicktime in cinelerra but is very buggy.

---

### Post by Limitlesschannels on 2007-05-31
whoops, sorry, use these instead, i didn't notice your architecture:

```

deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/ ./
deb http://archive.ubuntustudio.org/ubuntustudio feisty main

```

and apt-get update ; apt-get install cinelerra

the error is a GPG key thing; a pretty common error when you have thing added to your repo but not confirmed with a GPG key, anyway, it shouldn't be necessary for this once you have the correct architecture, so just try out the above one.

---

### Post by linuxnooby on 2007-05-31
[B][I]Code:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

then just apt-get install cinelerra.[/I][/B]


Followed your instructions and Cinelerra still will not run. No activity at all, when clicking on the application icon and  in the console, when I type cinelerra, the following message is returned :-

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen


???????

---

### Post by suoko on 2007-06-09
> **linuxnooby said:**
> [B][I]

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen


???????

I'm stuck too

---

