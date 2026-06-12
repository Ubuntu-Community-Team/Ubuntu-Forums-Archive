---
title: "Building a custom Distro based on Debian/Ubuntu"
date: 2011-06-24
forum: Any Other OS
---

### Post by Neko Linux on 2011-06-24
Hello everyone I have a few questions about building a custom Debian/Ubuntu distro. After digging around in the forums and searching I found a bit on software/scripts that can be used to build one. What I'm trying to do is build a OS for (mainly) Nettops and Netbooks, but can run on other systems. Somewhat like a Web/Cloud OS (Chrome OS/Jolicloud) but can also be used without the internet also.

What I want to do customizing wise.
-Custom background
-Strip it down a bit
-Remove and add software
-Custom Bootscreen
-Add the name of my distro to where Debian/Ubuntu is placed at
-Tweak boot up time


What I all found for software/scripts.
Remastersys
Novo Builder
Reconstructor

Which one, in your opinion is good? 
Are there any other besides these 3 for Debian/Ubuntu?

---

### Post by FormatSeize on 2011-06-24
Remastersys is normally the one that I see recommended. The other two I have never heard of. 
 
I'm also toying around with making my own distro for personal use, though I am likely going about it the wrong way. I'm winging it and thinking that I can combine things that are likely un-combinable. 
 
Question: for a Debian system, wouldn't it be easier to get something like Ubuntu Mini and install only the most basic packages and go from there rather than taking something and stripping it down? (I honestly don't know the answer to that question)

---

### Post by lykwydchykyn on 2011-06-24
On debian, I'd look at debian live helper.  I don't know if you can build an actual installer with it yet, but you can build a custom live CD/usb.  

You can also just run debian installer with a custom preseed script.

---

### Post by wolfen69 on 2011-06-24
Are you doing this for yourself, or do you plan to release it?

---

### Post by Neko Linux on 2011-06-24
> **wolfen69 said:**
> Are you doing this for yourself, or do you plan to release it?

For now, it will be just for myself. But later on I will release it.

---

### Post by wolfen69 on 2011-06-24
> **Neko Linux said:**
> For now, it will be just for myself. But later on I will release it.

I'm not trying to damper your enthusiasm as I think it's great your doing this, but there are *so* many lightweight/netbook type ubuntu based distros already. If you release it, try to make it different than the other 30 lightweight ubuntu/debian based releases. It's getting to the point where it's really hard to separate yourself from the pack.

But if nothing else, you'll have a nice custom distro for yourself.

---

### Post by Neko Linux on 2011-06-24
> **wolfen69 said:**
> I'm not trying to damper your enthusiasm as I think it's great your doing this, but there are *so* many lightweight/netbook type ubuntu based distros already. If you release it, try to make it different than the other 30 lightweight ubuntu/debian based releases. It's getting to the point where it's really hard to separate yourself from the pack.

But if nothing else, you'll have a nice custom distro for yourself.

It's going to be different then the other lightweight distros out there. Think of it as this. Chrome OS, but is more then just a browser that is google chrome. A distro that is fast booting, lightweight, can be used for work (not at an OS to replace other OSes at work, but can do work/schooling on), home, internet, or for multimedia center.

---

### Post by aerofly5 on 2011-06-25
I am so glad this thread exists. I was trying to compile the linux kernal from source. This seems like a much easier option :)

---

### Post by wolfen69 on 2011-06-25
> **aerofly5 said:**
> I am so glad this thread exists. I was trying to compile the linux kernal from source. This seems like a much easier option :)

It's a lot of fun to do, that's for sure. I have no plans on releasing an .iso any time soon, but I have a lot of respect for those that *are* serious about it. Kudos.

---

### Post by FormatSeize on 2011-06-27
> **wolfen69 said:**
> If you release it, try to make it different than the other 30 lightweight ubuntu/debian based releases. It's getting to the point where it's really hard to separate yourself from the pack.
True. But for starters, adding a command line text editor would at the very least grab my attention.

---

### Post by unknownPoster on 2011-06-28
> **FormatSeize said:**
> True. But for starters, adding a command line text editor would at the very least grab my attention.

Not sure what that means. Every Linux distribution in existence comes with vim/nano/pico/ed.

---

### Post by FormatSeize on 2011-06-29
> **unknownPoster said:**
> Not sure what that means. Every Linux distribution in existence comes with vim/nano/pico/ed.
eOS doesn't. Nor does SwiftLinux. I can't find the SwiftLinux website anymore, but there's a thread a couple pages down about it where I mention my shock at the lack of a command line editor. [Here it is.](http://ubuntuforums.org/showthread.php?t=1771832&page=2)

---

### Post by unknownPoster on 2011-06-29
> **FormatSeize said:**
> eOS doesn't. Nor does SwiftLinux. I can't find the SwiftLinux website anymore, but there's a thread a couple pages down about it where I mention my shock at the lack of a command line editor. [Here it is.]("http://ubuntuforums.org/showthread.php?t=1771832&page=2")

I don't consider SwiftLinux a valid distribution. If it expects to be taken seriously some major things need to change.

I can't find anything about eOS at all on Google, so I don't think it counts either.

---

### Post by FormatSeize on 2011-06-29
> **unknownPoster said:**
> I don't consider SwiftLinux a valid distribution. If it expects to be taken seriously some major things need to change.
Fair enough. 
 
> **unknownPoster said:**
> I can't find anything about eOS at all on Google, so I don't think it counts either.
Elementary OS. I'm not sure if that one really counts, either, but it's listed on Distrowatch, if that counts for anything.

---

### Post by cbowman57 on 2011-06-29
> **aerofly5 said:**
> I am so glad this thread exists. I was trying to compile the linux kernal from source. This seems like a much easier option :)

If you want a nice, fast desktop kernel look at this one [http://liquorix.net/](http://liquorix.net/)

---

### Post by cbowman57 on 2011-06-29
> **Neko Linux said:**
> For now, it will be just for myself. But later on I will release it.

I've found that starting with an Ubuntu live iso and using UCK (Ubuntu Customization Kit) is a very nice method.  It's what I use to do my respins, but I haven't bothered to mess with trying to customize the install.  My philosophy has been the closer I remain to the default Ubuntu installation look & feel the better, but I have seen it done very well.

---

