---
title: "[SOLVED] Installing a Ventrilo server"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by PotatoMasher on 2007-09-25
Hello guys!
I'm a total noob in Ubuntu systems, and I wanted to know step by step how to set up a ventrilo server on my fresh installation of ubuntu. 

My computer specs are here, if it help:
Intel Celeron A, 434.36 MHZ
320 mb SDRAM

Ubuntu runs fine, I just don't know how to set up a Ventrilo server as it is my first experience with Ubuntu...
:confused:
Thanks for your answers!!

---

### Post by wheredidrealitygo on 2007-09-25
Pulled directly from the ventrilo [website]("http://www.ventrilo.com/setup.php#Server_Installing")

    > 1) Open a terminal window (telnet or OpenSSH) to the host computer that will be running the server.

    2) Set your working directory to where ever you want to create the ventrilo directory.

    3) Type "mkdir ventrilo"

    4) Type "cd ventrilo"

    5) Copy the tar.gz file into this new directory.

    6) Type "gunzip " followed by the name of the tar.gz file.

    7) Type "tar xf " followed by the name of the tar file. (gunzip removed the gz extension).

    8) Note: Some platforms allow for combining steps 7 and 8 into a single command by typing "tar zxf " followed by the name of the tar.gz file.

    9) Type: "./ventrilo_srv".

This will start the server using default settings which should be more then sufficient for the normal user.

The ventrilo server does not have a GUI interface. All output will occur in the console window. The server can be configured to start automatically when the computer is rebooted. However, this will require root access in order to implement. Please read the "ventrilo_srv.htm" file with a web browser for details.

If you want to change any of the settings then you can issue the following command: "vi ventrilo_srv.ini". This will start the vi editor program and allow you to edit the INI file which defines how the server should operate.

Please read the "ventrilo_srv.htm" file with a web browser for more details about how to configure and tweak the server configuration.

It worked for me when I set mine up.

---

### Post by PotatoMasher on 2007-09-26
Thank you, "wheredidrealitygo"!

This really helps, as it is an easy walkthrough for a ubuntu noob like me!
I'll post the results of my work when it will work fine.:)

---

### Post by wheredidrealitygo on 2007-09-26
Sounds great PotatoMasher!

Hope it works out for you.

 if this works for you, could you mark the thread as being solved with the "thread tools" at the top section of the thread?

---

### Post by PotatoMasher on 2007-09-26
Yeah, oh course!
as you post, i'm trying to make it work with the Linux console as you suggested.
thanks again if it works, and i'll let you know if it don't!

---

### Post by PotatoMasher on 2007-09-26
Does anyone know how to configure properly the INI file settings?
I mean how to translate my server name in phonetic language, or even simpler, how to get a normal GUI interface (here I mean FRIENDLY USER!) if it is possible. 

Thanks for your compassion and your replies!!

---

### Post by wheredidrealitygo on 2007-09-26
You can open up any text editor (gedit, vim, nano, etc...) and edit the .ini file.

(example)

```
gedit /home/*username*/ventrilo/confi.ini
```

or something along those lines

The linux version of the server is only CLI (command-line interface, so non-gui). remember most people only ever see the client, which connects to the server. it's the client which provides the GUI. you're the only one going to see the terminal.

you can also do some configuration through the admin settings (with the password of the server) from the Ventrilo client.

We can try and answer any .ini related questions, if you post the .ini and ask about which option.

the max number of people that can connect with the free version is eight.

---

### Post by PotatoMasher on 2007-09-26
Thanks!
So my problem is now  how to configure the INI file, so I'm going to open up a new thread specific to this. See ya in this new thread, and thanks again!

---

