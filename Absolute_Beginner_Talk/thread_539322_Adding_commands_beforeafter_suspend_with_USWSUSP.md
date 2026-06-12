---
title: "Adding commands before/after suspend with USWSUSP"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Venerence on 2007-08-31
**[SOLVED]** - It turns out that the majority of problems were solved by disabling the ethernet connection, *especially* the command script to disable and re-enable the drivers. Without the need to wait until the wired gives up, the wireless reconnecting automatically wasn't a problem.

However, if anybody wants to resolve an unrelated issue, that's all good too. When I try to restart my computer, it freezes right before it shuts down (when the ubuntu backwards bar is empty). Shutdown works fine, starting back up works fine, restart however does *not* work.

Below is the original problem.
> Currently suspend works great using USWSUSP: I've implemented it as it describes [in this HOWTO](http://ubuntuforums.org/showthread.php?t=471855). Everything's working great, *except* wireless. I have to shutdown the drivers before the suspend and restart them after the resume.

Right now, my problem is this: I want to run the following command: ```
sudo modprobe -r ipw3945
``` right before USWSUSP suspends the laptop, and I want to run ```
sudo modprobe ipw3945
``` right after USWSUSP restores the laptop.

I've tried putting it into the acpi load area, but that did not work unfortunately.

Now here comes the strange part. My first idea was to put disable before the command to suspend, and resume afterward. After doing that, my hal-system-power-suspend-linux looked like this:
```
#!/bin/sh
sudo modprobe -r ipw3945
/sbin/s2ram --force
sudo modprobe ipw3945
```

After doing this and testing suspend, it still had the problem of connecting to the wired connection (which doesn't exist). However, this time around it saw the wireless networks. However, it would not let me connect to them, and upon trying it does not connect to either. Disabling and re-enabling the network allows it to connect, however.

After some testing, I have noticed this. As long as I re-enable the ipw3945 driver *after* the wired network 'connects' (it does not in fact connect, it just says it does), the wireless will work normally. If I try enabling it before, it will mess up the connection. Therefore, I will probably also need to find a way to disable my ethernet card (eth0). if anybody knows a way to prevent that driver from loading, that would be fantastic.

My guess is that trying to add it directly to the suspend command script is not working because it disables and re-enables it immediately. Or, scripts work completely different to terminal commands and I have no idea what I'm doing. So, how can I get it to disable the driver (with that command) right before suspend, and  re-enable right after USWSUSP does its thing?

---

