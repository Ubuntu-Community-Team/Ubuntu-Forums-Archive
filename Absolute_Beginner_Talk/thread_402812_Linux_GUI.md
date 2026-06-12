---
title: "Linux GUI"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by j2satx on 2007-04-06
What is a good GUI for one Linux computer to control the desktop of another Linux computer?

Thank you.

---

### Post by Origin415 on 2007-04-06
VNC comes preinstalled on Ubuntu, you can set up the computer which is sharing its desktop in Preferences -> Remote Desktop

For the computer which will be controlling the other, use the command which was given when you set up the first computer.

---

### Post by steve.horsley on 2007-04-06
It really depends on what you want to do. VNC can be used on two modes. Firstly, a remote user can gain access to the existing desktop of the machine. This for instance allows the local adn remote user to see the same desktop and argue over the mouse position. You enable this in  System->Preferences->Remote Desktop.

Another mode is where VNC gives the remote user his own desktop separate from the local screen. Packages like **vnc4server** provide this.

---

