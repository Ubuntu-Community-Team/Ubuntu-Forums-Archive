---
title: "Yet another stupid question - can't sh"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by h4m574h on 2006-12-23
Hey people!

I am trying to install nvidia drivers, but when I use the command: "sudo sh NVIDIA-Linux-x86-1.0-9631.run", it says: "sh: Can't open NVIDIA-Linux-x86-1.0-9631.run"

If I do it however without sudo it runs normaly and I get the message i need root privileges to continue the install

The thing is that if I use "chmod +x" it probably won't overwrite the current system settings (which I guess a driver display install MUST do...)

Does anyone know how to solve the problem?

---

### Post by Scorpuk on 2006-12-23
Try it this way:


```

sudo su
<password>
sh NVIDIA-Linux-x86-1.0-9631.run
```

After you type sudo su you become the root user and all commands are run as root.


Dunno if it will work, but worth a shot. :)

---

### Post by raul_ on 2006-12-23
I don't know about you but in my system i need to type
[code]
sudo su root
[/code

---

### Post by h4m574h on 2006-12-23
It's really odd, but it works now. O_O

Another question: What is the comand to close x server?

---

### Post by raul_ on 2006-12-23
ctrl+alt+backspace

---

### Post by h4m574h on 2006-12-23
Isn't that just restart x? What I meant is to close it so I can install the driver.

---

### Post by Scorpuk on 2006-12-23
raul_

For me, on 6.06, I just type sudo su. I guess they changed it for 6.10?

---

### Post by h4m574h on 2006-12-23
For me it works with just "sudo su", so I guess it's just a specific problem.

---

### Post by Scorpuk on 2006-12-23
Not sure if you need to stop the X server to install the driver. Linux is nothing like windows for driver installs.

When I updated my display driver I just installed and then restarted x server with the ctrl+alt+backspace.

---

### Post by po0f on 2006-12-23
h4m574h,

To stop X, log in with your regular user on a virtual console (Ctrl - Alt - F1-6) and type the following command:
```
[FONT="Courier New"]$ sudo /etc/init.d/gdm stop[/FONT]
```
INstall the driver, reconfigure X, and start X again with:
```
[FONT="Courier New"]$ sudo /etc/init.d/gdm start[/FONT]
```

---

### Post by h4m574h on 2006-12-23
@Scorpuk:
 
For me it says:
>   ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).



@po0f, Scorpuk, raul_

Thx for helping ^w^

---

### Post by Scorpuk on 2006-12-23
cool you got it working.

I also just realised I probbaly managed to install the driver as Automatix did it for me and it probably shut down the server...

---

