---
title: "Problems with apt-get Ubuntu picking up wrong configurations?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2007-08-02
Im using Ubuntu on a network that has a proxy. I'm able to connect to the internet fine but I can't run updates or use the terminal to issue commands like "apt-get"

I've taken a screenshot of the terminal and highlighted where I think the problem is. When I type "sudo apt-get update" I see the following screen:
[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Ubuntu/Screenshot-shaneshane-desktop.png[/IMG]

You can see that the IP address that Ubuntu is trying to use as the proxy is highlighted. 
**THIS IS NOT THE IP ADDRESS OF THE PROXY**

Is there anyway that I can change this so that it points to the right IP?

---

### Post by Papi-KB7VGW on 2007-08-02
Under >System>Administration>Software Sources you can choose a different mirror site.  Choose one that is close to you.  I had that happen when a mirror stopped being a mirror.

---

