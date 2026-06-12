---
title: "FTP GUI client with ssh tunneling?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Jonathin on 2007-11-06
My college has a whole bunch of servers. Some of the private servers, such as the one I am using for research, can only be accessed if I ssh into one of the main servers. For example I can do ssh jon@mainsever, once I get in there I can ssh FROM mainserver to jon@privateserver.

In WinSCP, all I had to do was put in jon@mainserver in the main screen, then click the "tunnel tab" and put jon@privateserver, and it would work. Then I could drag and drop files from my desktop directly onto the private server without having to ftp them over to the main server, and then ftp from main server to private server.

I cannot find a FTP client in linux that will allow me to do this. I really do not want to transfer files to the main server, and then ssh from there into the private server to get them there. I just want to be able to drag and drop (or click something simple on a GUI) so I can get files from my laptop to files on the private server when I am not on campus.

If there is a program that can do this in linux, can you please list both the program, and how to do it in that program.

Thank you very much.
Jon

ALSO: I downloaded ftpcube and couldn't figure out if it can do what I need. However, I installed it from their website, and I am not sure how to uninstall it (it is not in the Synaptic Package Manager. Any solutions?

---

### Post by hyper_ch on 2007-11-06
I use Konqueror for that...

And put in the address bar:
```

fish://user@domain

```

---

### Post by Jonathin on 2007-11-06
Okay, I can do fish://jon@mainserver, but now how do I get the main server to connect to jon@privateserver?

My first post might have been unclear. I can only ssh to the private server THROUGH the mainserver.

In other words it is kind of like this.
On local machine: ssh jon@mainserver.
Once connected to jon@mainserver, I run ssh jon@privateserver on the main server.

so if I hit ftp while I am connected to the privateserver, my lcd is jon@mainserver/home when I need it to be jon@localcomp/home

---

### Post by hyper_ch on 2007-11-06
oh... hmm..... good question....

Does Mainserver also have a desktop installed?

---

### Post by Jonathin on 2007-11-06
yes, it has KDE on it.

---

### Post by hyper_ch on 2007-11-06
then you could use X11 forwarding from your Mainserver to your workstation and call that way konqueror on your mainserver...

---

