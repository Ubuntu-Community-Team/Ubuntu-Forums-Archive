---
title: "Startup commands in WMaker"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by aggiechemist on 2006-02-23
I need some help making a certain command run when the system starts.

I would like it to start as I log into the system, and not before then. There are a few difficulties though:

1. My system uses Window Maker. I love it, but this is one of those times it can be tough.

2. The command needs sudo. Well, it needs to be run at the super user level. But I don't want to have to type in the password every time either.

3. It is just a command. A quick one time deal, not a program I need to run. So it doesn't have a nice dockable icon, and even if it did I would not know how to give it convenient superuser status.

Anyone got a clever idea?
The command I want to run is just
sudo iwconfig eth0 enc off

The reason I need to run it so late is that I have tried putting it into earlier scripts (like bootmisc.sh) but the system hasn't actually created eth0 yet, so it can't act on it. I figure if I do this when WMaker starts, eth0 will actually exist.

---

### Post by aggiechemist on 2006-02-24
All right, I fixed it. It was a fun challenge, and I finally sorted it out. Here is what I had to do:

1. Make a shell script.
cd /usr/bin
nano setenc
   #!/bin/bash
   iwconfig eth0 enc off

2. make it executable
sudo chmod +x /usr/bin/setenc

3. copy it to the init.d directory
sudo cp /usr/bin/setenc /etc/init.d/zsetenc

I changed the name. I'm not sure if if helped or not, but I need to process to be very late in the boot order. I had the idea it might be alphabetical, so putting it with a z might have moved it to the end. All I know is that it worked.

4. Make sure it is still executable.
sudo chmod +x /etc/init.d/zsetenc

5. Use rcconf to make sure it is part of boot
sudo rcconf

If you don't have rcconf, you can just install it with 
sudo apt-get install rcconf

And it worked!!! Hope this helps someone someday, it was mostly fun for me.

---

### Post by Stormy Eyes on 2006-02-24
Nice work. You could also try invoking it in an .xsession script, which I explain in [this howto](https://wiki.ubuntu.com/CustomXSession).

---

