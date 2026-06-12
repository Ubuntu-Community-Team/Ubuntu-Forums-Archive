---
title: "coding help with wake on lan instructions"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2007-06-22
I was given this bit of code to make the wake on lan function work. The problem is I am not a coder so can someone please let me know how I would create a start up file as described in the code in red
```


> First become the root user
> # sudo -i
> 
> Find the name of your ethernet port (most likely eth0) look for your ip 
> address
> # ifconfig
> 
> Issue the volitile command to enable magic packet wakeup (example if your 
> port is called eth0)
> # ethtool -s eth0 wol g
> 
> [COLOR="Red"]Create a startup file to always set this parameter
> # vi /etc/init.d/wol
> 
> ...and add the following between the ---'s
> 
> ---
> #!/bin/bash
> /usr/sbin/ethtool -s eth0 wol g
> exit
> ---[/COLOR]
> 
> Make the script executable
> # chmod 755 /etc/init.d/wol
> 
> Make the script run at startup
> # update-rc.d -f /etc/init.d/wol defaults
> 

```

---

### Post by molly_001 on 2007-06-22
Eddie:

Have you investigated in your BIOS as to whether Wake on Lan is enabled on the motherboard?  It is usually not enabled by default.  If you need help getting into the BIOS just let me know.

---

### Post by pmg on 2007-06-23
What the lines in red are telling you to do are create the file **/etc/init.d/wol** with the **vi** editor (you can use any editor you want.)  You'll need to use **sudo** to create a file in the /etc/init.d directory.  The content of the file should be```
#!/bin/bash
/usr/sbin/ethtool -s eth0 wol g
exit

```
The commands listed lower down, the **chmod** and **update-rc.d** will also require you to use **sudo**, e.g:
```
sudo chmod 755 /etc/init.d/wol
```

Another thing that you might find useful is running **sudo ethtool eth0** and look at the two lines with "Wake-on" near to bottom.  They will tell you what wol options are supported and enabled at the time, so:
>      Wake-on: g
means the wake-on magic packet is enabled (what you're trying to turn on.)  A value of **d** means WOL is disabled.

---

