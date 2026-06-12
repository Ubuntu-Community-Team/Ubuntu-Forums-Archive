---
title: "Minicom to Transfer ASCII cad files to CNC Mill"
date: 2008-10-06
forum: Art &amp; Design
---

### Post by PhillyStone on 2008-10-06
Hello, Thank you for the service you all provide to the community. I've been coming here for a few months now and you've almost always solved my problems from other users posts.

I wasn't sure where to post this but I figured since it is for an artistic purpose it fits. We are a small non-profit studio replicating artist renders into stone using CNC milling. I've been in the process of updating a lot of our hardware and software. Sadly the Milling Machines are a little old and communicate with the PC's through Minicom and a serial port. 

The problem arises with this. We've tried to update to XP machines but they mess up the ascii code in transmission. Sending the wrong X Y values. This is a problem because if a piece of stone is on the mill and gets the coordinate Y-0 it's going there no matter whats in the way. So we've been limited to only using win98 machines since they work properly.

So I talked my boss into giving a debian / linux system a try. Seeing as how it fits our needs. being much more secure to have on our network than a win98 machine and can be replaced easily if hardware fails. I loaded up one of the machines with ubuntu desktop x86 and installed minicom through synaptic.   

another big BUT! ... The CNC Mill has only a small memory cache and can only hold about 100 lines at a time so Minicom has to send it in a trickle feed. Win98 sends then waits for the num controller.. then once the line has finished. sends the next. When we tried to send over an ASCII on the ubuntu machine it kept trying to send the entire file at once. I can't find any auto detect or communication config.. so if anyone can point me in the right direction I would be grateful.

Thanks for reading my problem.
Mods: If this is in the wrong area I'm very sorry. please move it to a more appropriate home.

---

### Post by supirman on 2008-10-09
Are you using the ascii transfer mode to send the file?  If so, you can specify a delay between sending lines.

Go into minicom, then Ctrl+A, Z,  O for configure, then go to File transfer protocols.  In the line for ascii,  you see the line "/usr/bin/ascii-xfr -dsv ".  This is the command being called to send the file via ascii.  Edit that field, and make it look like
"/usr/bin/ascii-xfr -dsv -l 1000" to delay 1 second.  The delay is specified in milliseconds.

Hope that helps.

---

