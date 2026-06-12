---
title: "Micromedia Flsh Player???"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by dragon4021 on 2007-11-06
Ok I need Micromedia flash player to view some websites. Is there another program I should be looking for, because I can't find a .deb file for Micromedia.

---

### Post by rudeboyskunk on 2007-11-06
Make sure all of your repositories are enabled by going to System>Administration>Software Sources.  Then go to System>Administration>Synaptic Package Manager and search for "flash."  It's something like "flashplugin-nonfree" or something.

Or, optionally, after enabling your repositories, open up Firefox, go to a page that requires flash, and at the top of the page there will appear a button asking you to install the missing plugin (i.e., flash).

EDIT:  And one problem might be that you're spelling it Micromedia.  It's Macromedia, with an a.

---

### Post by dragon4021 on 2007-11-06
I enabled the flash package you told me about, but that didnt fix the problem. It's mainly myspace which im trying to access the videos.

---

### Post by rudeboyskunk on 2007-11-06
Try to install mozilla-flashplugin (or something similar to that, just do a search in Synaptic for "mozilla flash").

---

### Post by LinuxGuy1234 on 2007-11-06
> **dragon4021 said:**
> I enabled the flash package you told me about, but that didnt fix the problem. It's mainly myspace which im trying to access the videos.

Go to: [http://www.adobe.com/]("http://www.adobe.com/")

then download the Flash Player and install that. Or try Gnash, but that only plays up to version 7 SWF's, which Flash MX makes.

---

### Post by aysiu on 2007-11-06
> **dragon4021 said:**
> I enabled the flash package you told me about, but that didnt fix the problem. It's mainly myspace which im trying to access the videos.
"[T]hat didn't fix the problem"? Can you be more specific? After installing the problem, what appears on your screen when you visit MySpace?

---

### Post by dragon4021 on 2007-11-06
Neither worked! This is so damn fustrating. Lol When I go on to myspaceit just says down load the latest macromedia flash payer where the video is supose to be.

---

### Post by aysiu on 2007-11-06
Close Firefox

Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
rm ~/.mozilla/plugins/*flash*
sudo apt-get remove mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree
``` Then start Firefox again.

If one of those commands gives you an error message, just keep going with the other two, but copy and paste the error messages/output back to this thread.

---

