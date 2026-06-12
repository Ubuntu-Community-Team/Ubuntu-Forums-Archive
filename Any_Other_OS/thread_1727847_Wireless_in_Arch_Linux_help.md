---
title: "Wireless in Arch Linux help"
date: 2011-04-13
forum: Any Other OS
---

### Post by Jakerules on 2011-04-13
Hey,
Just got Arch Linux installed on my computer and managed to install it pretty alright on virtualmachine before. But I forgot one of the most basic things that I didn't need to know how to do before and that's how to get my wireless running!

I'm looking it up online and there's so many different ways of doing this that it's confusing me.

What's the most simple way to get my wireless running on Arch Linux? I have access to a wired connection to get it started as well.

Thanks guys
Edit for a little more details: 
My netcfg configuration is working and whenever I use netcfg mynetwork it says the error

SIOCSIFFLAGS: Unknown error 132
Could not set interface 'wlan0' up

Update: Went into bios and switched off my laptops wlan switch. So now it's always on. Fixed that error, but now I get..

find: `/var/run/network//suspend/': no such file or directory

Final edit: Haha, fixed it with dumb luck. Created an empty folder in var run network suspend and now it works!

Sorry for wasting your time if you read this!

---

