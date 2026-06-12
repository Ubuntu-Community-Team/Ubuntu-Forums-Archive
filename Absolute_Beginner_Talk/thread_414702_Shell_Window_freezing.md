---
title: "Shell Window freezing"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by drhiii on 2007-04-20
Question about... I open up a shell window, then ssh to a server.  I haven't really timed it, but after approximately 5-10 minutes of inactivity, meaning if I have run off and done something else in Gnome, if I come back to the shell window, it is unresponsive.  I ran a ping just to keep activity in the window and it appeared to help keep it from freezing.  But if there is no activity in the window for a few minutes, when I return to it, nuttin'.  I have to close the window and restart whatever I was doing.

Thoughts anyone?  I've surfed around but have not found anything on this.

Oh, shell window is a term I learned for Terminal Window.  Same thing.

tx

---

### Post by skelooth on 2007-09-08
I'm having the same problem, so if anyone has any idea?

I'm trying to remotely use mysql and gedit, and if either is left untouched for more than a bit it freezes and has to be xkilled.

---

### Post by drhiii on 2007-09-08
> **skelooth said:**
> I'm having the same problem, so if anyone has any idea?

I'm trying to remotely use mysql and gedit, and if either is left untouched for more than a bit it freezes and has to be xkilled.


Add the following lines to your /etc/ssh/ssh_config as this appears to work for me.  Keeps the connection alive, no freezing...

    KeepAlive yes
    ServerAliveInterval 30

---

### Post by skelooth on 2007-09-08
> **drhiii said:**
> Add the following lines to your /etc/ssh/ssh_config as this appears to work for me.  Keeps the connection alive, no freezing...

    KeepAlive yes
    ServerAliveInterval 30

Thank you, does this go in the server or client configuration?

---

### Post by schorsch on 2007-09-08
The file "/etc/ssh/ssh_config" is used for the client config whereas the file "/etc/ssh/sshd_config" is used for the server config. So the advice is to alter the client config and I am testing it right now .. ;-)

---

### Post by schorsch on 2007-09-08
Well, it seems to work like a charm. Thanks for the advice!

---

### Post by drhiii on 2007-09-08
> **skelooth said:**
> Thank you, does this go in the server or client configuration?

This goes in the client configuration.   ssh_config   

One could apply something similar to to the sshd_config file, but that is for incoming connections.  Hope this works for ya....

---

### Post by skelooth on 2007-09-08
> **drhiii said:**
> This goes in the client configuration.   ssh_config   

One could apply something similar to to the sshd_config file, but that is for incoming connections.  Hope this works for ya....

Thank you very much, it solved my problems perfectly.

---

