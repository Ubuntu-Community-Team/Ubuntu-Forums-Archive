---
title: "sudo in an Application Launcher"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by sgood on 2007-07-07
I created an application launcher, however because the application needs to be started with sudo I had to make it launch in a terminal window.  Is there a way to pass the password along with sudo so that I can launch the application without the terminal window being open while the app is running?

Thanks in advance,  
~Steve

---

### Post by felicity on 2007-07-07
I'm not sure about that but you can use "gksu applicationname" in your launcher to launch the program still. (it will open a password dialog box though)

---

### Post by kerry_s on 2007-07-07
gksu or gksudo, you can also create a group and add it to the sudoers with "NOPASSWD" then you can use gksudo without using a password. recommended for gui apps only and if your not worried about physical access. i use it for root tasks.

---

### Post by sgood on 2007-07-07
@ kerry_s

I'm not sure what I would add to the file you should in your thumbnail.

Here's the details of what I am trying to do.

start the app using this string

sudo /opt/jrun4/bin/jrun -start cfusion

it runs as nobody:nobody

once running it stays in the background since it's just an IDE for CFML (Similar to a PHP server)

currently I have the above line in my application launcher and the TYpe is set to "Application in Terminal"

I want to change the Type to "Application".  I have Coldfusion running on a server, but it starts automatically.  The only option I can think of is to set it to autostart, but I don't want it taking my laptop's resources unless I am actually using it, hence the app launcher.

I tried both gksu and gksudo in the launcher, but neither of them will actually start the app.  I tried in both Application and Application in Terminal types with no luck.

~Steve

---

### Post by neptho on 2007-07-07
> **sgood said:**
> @
I tried both gksu and gksudo in the launcher, but neither of them will actually start the app.  I tried in both Application and Application in Terminal types with no luck.

~Steve

Double check that your environmental variables are properly set.

---

### Post by sgood on 2007-07-07
I'm not sure what you mean...  Where should I be looking?  And what exactly should I be looking for?

---

### Post by neptho on 2007-07-07
> **sgood said:**
> I'm not sure what you mean...  Where should I be looking?  And what exactly should I be looking for?

When you login as your normal user, open a terminal, and run this:

```
set | less
```

You'll see many settings.  These are environmental variables, quite similar to what you may or may not remember in DOS and Windows.

When you run something as root, depending on how you launch it, it may, or may not inherit these settings.

A general rule of thumb is that gksudo should, gksu won't.  You can try debugging it by running this from a Terminal:

```
gksudo -d -k -S -u root /opt/jrun4/bin/jrun -start cfusion
```

---

### Post by sgood on 2007-07-07
So I ran the debugging command you posted and this is the output it gave me.

```
No ask_pass set, using default!
xauth: /tmp/libgksu-428KdU/.Xauthority
STARTUP_ID: gksudo/|opt|jrun4|bin|jrun 'cfusion'/11029-0-dell-700m_TIME7520165
cmd[0]: /usr/bin/sudo
cmd[1]: -S
cmd[2]: -p
cmd[3]: GNOME_SUDO_PASS
cmd[4]: -u
cmd[5]: root
cmd[6]: /opt/jrun4/bin/jrun
cmd[7]: cfusion
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
        at java.lang.Class.getMethod(Class.java:986)
        at jrunx.kernel.JRun.invoke(JRun.java:179)
        at jrunx.kernel.JRun.main(JRun.java:168)

Usage: -[start,stop,restart,status] [server ...] (no arg means all servers) or -[stop,restart] server [server ...] -username <jndi-principal> -password <jndi-credentials> or -info or -version or -usage
xauth: /tmp/libgksu-428KdU/.Xauthority
xauth_env: /home/sgood/.Xauthority
dir: /tmp/libgksu-428KdU

```

It seems like it's not picking up the -start flag or the cfusion variable...  I'm not sure what I need to add / change to get those two things to be passed in the command.

---

### Post by sgood on 2007-07-07
Nevermind I figured it out.  I needed to remove the - from the start flag.  it's all working now, thanks guys!

---

