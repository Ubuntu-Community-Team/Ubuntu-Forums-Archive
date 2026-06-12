---
title: "Remote Desktop help"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by SavageFreedom on 2007-06-18
Hello,

I recently installed Ubuntu Feisty onto my mother's new computer in Chicago. I live in Saint Louis. As I can't be there to help her figure it all out, it would be VERY handy to be able to remotely connect, but I'm not sure how that works. She uses Gnome, I'm using KDE. I know about vino and VNC, but it seems that when she uses the "Remote Desktop" settings in Ubuntu, it is only going to allow users on a local network to log into her machine. The command it tells her to give me is "vncviewer elektra-desktop:0" ... obviously of no use to me since I'm in a different state on a different machine.

How do I connect to her from a distance like this? I've seen other people do it, so has she, but never with linux. Help me help my mom help herself!

---

### Post by zanglang on 2007-06-19
First you'll need to make sure that she's not behind a firewall/router, and if so open up and forward port 5900 accordingly. Test if that port is contactable by outside computers here: [http://whatsmyip.org/ports/](http://whatsmyip.org/ports/)

Next, you need to get her current internet IP. Ask her to visit this page: [http://whatismyip.com/](http://whatismyip.com/) and send you the results.

Then type the command to connect:
> vncviewer <her IP address>
Alternatively you can try using the 'Terminal Server Client' in the Internet menu.

For more info, check this page perhaps: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

