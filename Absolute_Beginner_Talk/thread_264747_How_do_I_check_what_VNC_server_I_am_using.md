---
title: "How do I check what VNC server I am using?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-09-25
How do I check what VNC server I am using?

I'm guessing that vino is installed as the default VNC server in ubuntu, and I did install VNC4Viewer (or something called similar to it by adding extra repositries) but I don't know which I am using.

I'm guessing that seeing as I didn't configure anything for the latter, that I must be using vino, and I'm wondering if this is why it's extremely slow over SSH.

---

### Post by bernied on 2006-09-25
After starting vncserver, try:
ps -ef | grep vnc
That will give you the applicaton that is called.

When you say it's slow over ssh, is that on the LAN or over t'internet?

---

### Post by DarkKoopa on 2006-09-25
Over the internet.

It's like using pcAnywhere (Windows) over a dialup connection.

I did the command and got this

> XXuserXX 6352 6328  0 20:23 pts/1    00:00:00 grep vnc

I hope that means something to you. :\\\:???:

---

### Post by bernied on 2006-09-25
That output  means that the only process running that has vnc in it, is the one that you started to look for it.

ps lists running processes - the ef option says tell me about (e)very user, and tell me the (f)ull command that was used to start the process. grep is a search function, and | pipes the results of ps to grep. So the result is a list of all processes that have 'vnc' in them.

Was the vnc server running when you typed that command?

If it was, try it with vino instead:
ps -ef | grep vino
Or try it without the grep:
ps -ef

The vnc over the internet will be as slow as the slowest link in the chain that joins the vnc server pc to the vnc client pc - so probably the upstream speed of the connection from your home pc to your isp. vnc sends rectangular images of parts of the screen that have changed since it last updated, images use lots of bandwidth. You can use a smaller screen size to make it a bit faster, but you lose bandwidth. You can also change the jpg compression.

---

### Post by DarkKoopa on 2006-09-26
Thanks for your help.  In my impatient state, I installed FreeNX and am using that instead.

Thanks again anyway, you deserve a :KS 

PS>  Thaanks for explaining that code, it should come in handy now I know what it means.

---

### Post by motin on 2006-10-08
Great you use FreeNX now, but the answer to your original question is to execute the following once the server is up and running:

```
 sudo netstat -ap | grep LISTEN | grep -v LISTENING

```

There you can see what apps are listening on what ports etc.

---

