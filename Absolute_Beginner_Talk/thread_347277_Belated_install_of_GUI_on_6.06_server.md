---
title: "Belated install of GUI on 6.06 server"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-01-27
I have ubuntu server 6.06 installed on a file server at home, but now I want to hook up another printer to it so that it can serve all of my print needs.

I was told that ubuntu printing leaves a bit to be desired, I am ok with documents but would eventually like to print pictures etc...

I have a canon720cc hooked up to my desktop now, and want to hook up my wifes Epson880 to the server as well as my canon, and a canon pixma to the ubuntu server.

I figured I could install a GUI onto my ubuntu server and then install XP through VMWare so that I could print through XP

Does anyone know how to install the GUI onto my server box after the fact, or are the printing worries I have unfounded?  Is linux capable of printing high quality prints?

btw my wife uses a MACBook for her stuff.

Im sure my post is a bit contrived if there are any questions I left out please ask.

Hopefully I dont need to install XP and ubuntu can take care of all of my printing needs.

Thanks in advance...

---

### Post by irish_flu on 2007-01-27
All I can say aabout printing in Ubuntu (because I don't ahve much experience with it) is that Ubuntu prints nice-looking pages onto my HP shared from my Windows box (and it set up in a snap, too!).

As far as installing a gui onto the server, you just need to use the command "sudo apt-get install ubuntu-desktop"

EDIT: forgot the "sudo"

---

### Post by charles.g.moore on 2007-01-27
Thanks for the heads up on the GUI install, I wish I could find some concrete info on printing with ubuntu.  I dont necessarily want to install XP through VMWare just for printing...

---

### Post by irish_flu on 2007-01-27
You know what?  I gave you the wrong command anyway.  Sorry about that, it's been a long day.

The correct command (which I'll fix in my other post too) is 

sudo apt-get install ubuntu-desktop

---

### Post by charles.g.moore on 2007-01-27
cool ill be sure to use it tomorrow...

---

### Post by Soarer on 2007-01-27
You can check for printer compatibility on [http://openprinting.org/](http://openprinting.org/) - according to that the Epsom PM 88c works 'perfectly'.

For a GUI on your server, maybe [Webmin]("http://www.webmin.com/") would do the job. You can configure lots of things, including printers, from your desktop's browser, but it is lighter on the server than a full desktop environment. Works fine on Dapper & Edgy, but isn't in the repos.

---

