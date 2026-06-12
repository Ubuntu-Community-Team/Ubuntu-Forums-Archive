---
title: "Can't make gcc to work – install"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by godlike_panos on 2006-08-28
When I type “gcc” I get “command not found" error so I checked if I had gcc installed. 

In Synaptic P. M. under development I see that a package named gcc-4.0-base is installed. 

When I type “apt-get install build-essential” I get always “Package build-essential has no installation candidate”. I saw a solution somewhere in the forum in which they change the sources.list and then “apt-get update” but I don't have net at this point.

I also went to gcc.gnu.org to see if I can find a way to install gcc manualy. I downloaded a colossus archive but I cant compile it.


Does anyone have an idea.
Thanks in advance!

---

### Post by MrHorus on 2006-08-28
> **godlike_panos said:**
> 
When I type “apt-get install build-essential” I get always “Package build-essential has no installation candidate”. I saw a solution somewhere in the forum in which they change the sources.list and then “apt-get update” but I don't have net at this point.

There should be a CD with additional content; you could use that to install any packages although really it's best to get them online so that you have the latest versions plus any relevant security updates.

---

### Post by elettronicha on 2006-08-28
> **godlike_panos said:**
> When I type “apt-get install build-essential” I get always “Package build-essential has no installation candidate”. I saw a solution somewhere in the forum in which they change the sources.list and then “apt-get update” but I don't have net at this point.
I figure you have to add some extra repository to your sources.list. Try searching the official documentation to know how to, but you need to have the net. Also you can download and install this packages: [http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential)

---

