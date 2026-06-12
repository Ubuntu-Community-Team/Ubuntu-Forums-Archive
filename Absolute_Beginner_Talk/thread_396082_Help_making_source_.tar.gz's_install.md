---
title: "Help making source .tar.gz's install"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by JimmyHopkins on 2007-03-29
Ok, I can't get this right. I've tried skype, xmms, and frostwire, and I can't get them to install (yes, I know I can synaptic them, I want to ensure I can install source code). I move the term to /home/X/desktop/whatever, and do ./configure. nothing ('cept for xmms). I then to make. nothing. I ALWAYS get "make: *** No targets specified and no makefile found.  Stop." I've downloaded bulid-essential fron synaptic, so what's wrong? Thanks for any help (this is a pain).

---

### Post by aysiu on 2007-03-29
Why don't you install XMMS from Synaptic?

**Step 1**: [Enable extra repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

**Step 2**:
Install XMMS the same way you installed *build-essential*

For Frostwire, paste these commands into the terminal: ```
wget -c http://www.frostwire.com/download.php?file=http://www.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.6.i586.deb
sudo dpkg -i frostwire-4.13.1.6.i586.deb
```

For Skype, paste theses commands in: ```
wget -c http://download.skype.com/linux/skype_debian-1.3.0.53-1_i386.deb
sudo dpkg -i skype_debian-1.3.0.53-1_i386.deb
``` Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by JimmyHopkins on 2007-03-29
No, you miss the point. A lot of stuff I've run into the past was source-only. I want to be able to install source. It's more about education.

---

### Post by aysiu on 2007-03-29
> **JimmyHopkins said:**
> No, you miss the point. A lot of stuff I've run into the past was source-only. I want to be able to install source. It's more about education.
Sorry. You're right. I overlooked this part of your original post: > (yes, I know I can synaptic them, I want to ensure I can install source code) I guess the only thing I can think of is that a lot of time .tar.gz files are not source packages but just zipped-together files for a precompiled binary.

---

### Post by JimmyHopkins on 2007-03-29
Oh well. I'll go huntin for source tonight.

By pre-compiled biunaries, you mean stuff like (windows) .exes, .sh, .deb, .rpm, etc?

OT: I just discovered scripts tonight! Yay. I love ubuntu. Too bad my 360 is the latest kernel, or otherwise I'd have ubuntu on it too. Seriously, great job. Better than POS fedora core (FC looks like windows compared to ubuntu).

---

### Post by Slodeine on 2007-04-21
I'm having the same kind of problem installing Thunderbird 2.

It came as a .tar.gz file.  I extracted it, and tried to follow the normal procedure for compiling source files, but I received the same errors as Jimmy.

How do you install these pre-compiled binaries?

---

### Post by bobplano on 2007-04-21
well to make a file there has to be rules to make it. if it doesn't come with something like a makefile then make won't work. i think you also need linux headers and gcc and cpp (for the libraries) so run this 
```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```
even if it still doesn't work you then have everything you need to "make" other things

---

