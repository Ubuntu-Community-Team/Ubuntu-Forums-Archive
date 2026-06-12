---
title: "How can I change my VNC Server Listening Port"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-11-04
I have vino installed and I need to change the listening port on one box so that I can vnc into multiple boxes on my network.  How can I do that?

---

### Post by necrit on 2007-11-04
Found the answer [http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/](http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/)

---

### Post by kc5hwb on 2007-11-10
I gave that to you >:o

---

### Post by necrit on 2007-11-10
hrm.  ANYWAY.  i just looked and vino doesnt respond to that like it should.  again the age old question where's the other conf file if THIS one isnt getting the display changed.  Like we talked about it msg it appears that vnc4server has a MUCH better sucess rate

```

apt-get vnc4server xinetd

```

---

### Post by kc5hwb on 2007-11-11
GAC that.... vnc4server is available through Synaptic.  And yes, I will go ahead and install that today, but you might have to help me conf it because I am sure that you will be foaming at the mouth with a bongalicious desire to raid the server again, only to find that you can't login because it isn't conf'd.  :mad:

---

