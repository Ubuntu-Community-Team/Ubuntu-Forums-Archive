---
title: "VNC multi-connect"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Threbus5 on 2006-12-22
HI,
I have read several threads and howto's on configuring VNC for multiple instances including a pretty thorough one about sharing desktops with x11vnc.

A friend told me that if VNC were running, each successive login to the server should (would, is supposed to) generate a separate desktop for that user.

Well, I must have missed something vital and simple because although VNC seems setup for two logged in users and two users can login each to a separate session (session 0 and 1), only one user has an active desktop. The user that is on the active displayed monitor screen on the "server" can control the desktop from their client. The other user has a blank screen with a movable cursor.

I read two notes. First to "su gedit to etc/sysconfig/vncserver..." and add accounts. There is no sysconfig directory in the root etc directory. Also the same thread said to follow the path "applications , system, server settings, services and enable the vnc server" However, the dapper menu choices are - applications, system, admin, services - and VNC server is not listed as a service.

I feel as if someone has nailed one of my feet to the floor and is marching me around in circles.

How does one initiate "multiple instances" of vnc server?
Is that what I really want? (I do not know enough to know if it is.)
How do I run the VNC as my friend described - that is, allow two or more simultaneous logins that each has a separate desktop?

Thanks and Merry Christmas.

And it is a Merry Christmas,

I found the vnc4server  thread and vnc4server does exactly what I need.

Bye.

---

