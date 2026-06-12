---
title: "Running a script as root without password?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-09-18
I am using a script to launch Enemy Territory because there is a problem with the sound.

I don't mind that. The only thing that annoys me is that part of the script needs to be run as root. This is the script:

```

#!/bin/bash
gksudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
gksudo echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
X :1 -ac & DISPLAY=:1 et
esd
exit 0

```

This annoys me because it has to get my password when I want to run the game. While I can live with this, can anyone suggest a way to avoid it without disabling the sudo password for my user?

Oh, by the way, the line that actually launches the game would be much less complicated but I start a new X session for my 3d games so that they don't conflict with XGL.

---

### Post by Poeffie on 2006-09-18
Did you give the user permission to execute the file and tried that?

sudo chmod +x <filename>

try executing the script now, with the regular user

---

### Post by steve.horsley on 2006-09-18
The obvious thing to do is to make your script setuid root. That is, make it owned by root, and set the setuid attribute on the file (chmod +s filename). But the kernel won't run scripts as setuid, so you will have to  compile an executable and make that setuid instead.

Install the compiler:
**sudo apt-get install build-essential**

create a file called runner.c, with these contents - change the name of the script to match the path of your script you want to run:
```

main(int argc, char** argv) {
    system("/home/me/myscript");
}

```
Compile the C program:
**cc runner.c**

This creates a file called a.out. You need to make this owned by root and setuid:
[B]sudo chown root a.out
sudo chmod +s a.out[/B]

Now you can run a.out and it will run your script with root priviledge:
**./a.out**

You probably want to rename a.out to something more sensible.

---

### Post by edrodgers731 on 2006-09-18
> **pbaehr said:**
> I am using a script to launch Enemy Territory because there is a problem with the sound.

I don't mind that. The only thing that annoys me is that part of the script needs to be run as root. This is the script:

```

#!/bin/bash
gksudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
gksudo echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
killall esd
X :1 -ac & DISPLAY=:1 et
esd
exit 0

```

This annoys me because it has to get my password when I want to run the game. While I can live with this, can anyone suggest a way to avoid it without disabling the sudo password for my user?

Oh, by the way, the line that actually launches the game would be much less complicated but I start a new X session for my 3d games so that they don't conflict with XGL.

Although it's dangerous, setuid used to be the common way to do this.  This way the script will be run as root based on the permissions.

chown root:root foo
chmod 4511 foo

---

### Post by pbaehr on 2006-09-18
Good solution. I am going to wait to test it until I get home since I can't run the game over SSH.

One other thought, though.

/proc gets rebuilt every time the computer starts, right? Is there someplace I could put those lines so that they are added to /proc on startup rather than when the game launches? They don't seem to hurt any of the other sound on the system.

---

### Post by pbaehr on 2006-09-18
I added a script to /etc/init.d which will add those two entries to /proc.

Restarting the system now. I'll report back on if it worked.


Reporting back:

Yeah, it didn't work...

Reporting back again:

I realized I forgot to create a link in /etc/rcs.d. After I added that it worked fine. Now, hopefully there won't be any unforseen issues.

---

