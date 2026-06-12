---
title: "Lost Gimp default brushes, wont bring them back after reinstalll..."
date: 2007-06-14
forum: Art &amp; Design
---

### Post by Damarius101 on 2007-06-14
Ok, this is how it happend. I was trying to get new brushes for the Gimp (maybe some of you have heard of the 1100 free brushes download) and i think i accidentally wrote over all my default brushes. The thing is, it wont even recognize the new ones; seems like it will not read the folder i assigned them to. I go to File>Prefernces>Folders>Brushes, select the add folder button (one with the little dots), select the folder, hit ok, but when i restart they are not there.

Does anyone know what the hell is going on? I probably know why my brushes disappear, but when i reinstall Gimp with Synaptic Package Manager, it doesnt come back. Im a little frustrated, so all help is a appreciated :)

---

### Post by FRuMMaGe on 2007-06-14
I think this is because gimp uses the brushes in your home directory.  Just open up your home folder and type Ctrl+H to show hidden folders, then search for .gimp

try running gimp as another user to check if this theory is correct

---

### Post by Damarius101 on 2007-06-18
Ive done this, but when i open up the folders, there is nothing in any of them (plugins, fonts, brushes, nothing is in any of the folders). I have about 400 fonts that i use that still work, but when i go to the gimp font folder, there are gone. Ill try changing the user to see if theirs any difference though.

---

### Post by ComplexNumber on 2007-06-18
did you reinstall all the gimp stuff (eg gimp-extras etc)? 

i don't know precisely why this is happening, but your brushes are stored in *~/.gimp/brushes* and* /usr/share//gimp/2.0/brushes*

i'm wondering if something has gone slightly strange and your brushes or brushes folder(s) have become read-only, somehow. check the permissions in both folders, just in case. if you somehow overwrote your brushes in your home directory with root permissions, it won't see your brushes stored in your home directory. 

it would probably point to a permissions or ownership problem

---

### Post by FRuMMaGe on 2007-06-18
Try going onto the synaptic package manager, and instead of removing it, click "Completely Remove Package".  This will delete all configuration files aswell.

Now reinstall and try again

---

### Post by Tsega on 2007-07-27
Hello people I have the same problem. I did the same thing I copied the whole gimp brushes folder I had on my Windows machine to my Ubuntu machine, I said yes when the system asked me if I wanted to over-write the existing ones and I said yes. Restarted the GIMP and I found out that my brushes were gone. I tried to uninstall the GIMP and it said something like there is a dependency problem etc., so I just gave up and came to you guys.
I'll  try your suggestions and I'll tell you all about it. Thanks.

---

### Post by Tsega on 2007-07-28
Whoops! Here's what I did. 
1. First of all when I copied the brushes , I copied them to** /usr/share/gimp/2.0/brushes/brushes** and that was because I copied a whole new brushes directory into the already existing brushes directory.
2. So I just copied all the brushes from the** /usr/share/gimp/2.0/brushes/brushes** directory to just the **/usr/share/gimp/2.0/brushes** directory.That's where it should be.
3. Started the gimp and the brushes were there.

Maybe that's the problem Darius.

---

