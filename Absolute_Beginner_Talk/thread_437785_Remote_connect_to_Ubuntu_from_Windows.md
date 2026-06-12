---
title: "Remote connect to Ubuntu from Windows"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by hendysg on 2007-05-09
Hi,

I am trying to set up my ubuntu machine at home so that I can connect to it from my windows machine at work. 

I followed the instruction from [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine") and I was able to connect to my ubuntu machine from a windows machine at home (inside the same router) using vnc viewer running on the windows machine. 

My understanding is that if I want to connect from work, i need to forward port 5900 on my router. But port 5900 is already being used by my roomate to enable his vnc connection. Therefore I need to pick another port.

Now my question is, how can I set my ubuntu to use a different port, say port 5901, for vnc?

Also, if there's a better way to connect to ubuntu from windows other than vnc, please let me know. 

Thanks a lot,
-hendysg

---

### Post by hyper_ch on 2007-05-09
Well, on your router you should be able to forward an external port to a localport...

e.g. incoming connection on port 5901 should be forwarded to your local computer on port 5900

If you can setup that (which I think is a standard feature nowadays) then you don't need to change anything in your ubuntu machine :)

---

### Post by fakie_flip on 2007-05-09
Using putty from work to connect using ssh is another way. You need to install openssh-server on your Ubuntu computer for that. If you try to connect from work, you need to port forward port 22.

---

### Post by fakie_flip on 2007-05-09
You can change the port the vino server for vnc uses in Ubuntu.

[http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/](http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/)

---

### Post by hendysg on 2007-05-10
> **hyper_ch said:**
> Well, on your router you should be able to forward an external port to a localport...

e.g. incoming connection on port 5901 should be forwarded to your local computer on port 5900

If you can setup that (which I think is a standard feature nowadays) then you don't need to change anything in your ubuntu machine :)

Yeah. My router doesn't allow me to map external port to a different internal port.

---

### Post by hendysg on 2007-05-10
> **fakie_flip said:**
> Using putty from work to connect using ssh is another way. You need to install openssh-server on your Ubuntu computer for that. If you try to connect from work, you need to port forward port 22.

I wanna be able to see my entire desktop gui, instead of just using command line.
Is there a way to use ssh to do that?

---

### Post by hendysg on 2007-05-10
> **fakie_flip said:**
> You can change the port the vino server for vnc uses in Ubuntu.

[http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/](http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/)

Thanks fakie_flip. That helps. I am now able to use a different port.
Unfortunately, I think the corporate firewall at work prevented vnc from establishing connection.

---

### Post by fakie_flip on 2007-05-10
> **hendysg said:**
> I wanna be able to see my entire desktop gui, instead of just using command line.
Is there a way to use ssh to do that?

Yes, there is. It is called X forwarding with ssh. Here is an example of how it can be done. I logged into my brother's Linux computer from mine. To use X forwarding, you must have -X option for ssh when connecting.

ssh -X -l user serverip

After putting in the password (if im not using keys), I can run a program on his computer, and it will show up on mine.

gksu synaptic &

That will launch synaptic running on his computer, but it will show up on mine. I can install software using Synaptic, and it will be installed to his computer, not mine.

Edit: I re-read what you wrote. No you can't see the entire desktop gui, but you can run individual apps.

---

### Post by fakie_flip on 2007-05-10
> **hendysg said:**
> Thanks fakie_flip. That helps. I am now able to use a different port.
Unfortunately, I think the corporate firewall at work prevented vnc from establishing connection.

Are you sure it is not your router that isn't properly configured? You may have a friend run nmap from his computer to yours to see if he sees the vnc server running on your computer. That would mean that the port is opened and router properly configured. The reason I say friend is because you need someone who is outside of your network to test it. You said that your jobs firewall may be blocking it, but usually firewalls blocking incomming connections, not out going, so you may want to do some tests to find out for sure.

---

### Post by fakie_flip on 2007-05-10
Another possibility is that your ISP blocks incomming connections on certain ports. My ISP does that even though they did not admit it to me when I asked, but there is a solution. My solution was to run my apache web server on another port other than 80. I choose 9000. That required people who wanted to view my website to have to type [http://url:9000](http://url:9000) or [http://ipaddress:9000](http://ipaddress:9000), but I then found a solution to that problem. I signed up for an account at no-ip.org and used port redirecting.

---

### Post by hendysg on 2007-05-13
> **fakie_flip said:**
> Another possibility is that your ISP blocks incomming connections on certain ports. My ISP does that even though they did not admit it to me when I asked, but there is a solution. My solution was to run my apache web server on another port other than 80. I choose 9000. That required people who wanted to view my website to have to type [http://url:9000](http://url:9000) or [http://ipaddress:9000](http://ipaddress:9000), but I then found a solution to that problem. I signed up for an account at no-ip.org and used port redirecting.

Wow, thanks. I'll try your suggestions. I'll let you know if can/cannot make it work.

Thanks a lot.
-hendysg

---

### Post by hendysg on 2007-05-14
Thanks all for helping. I've set up my work and home computer to use ssh tunneling and vnc to remote connecto to my ubuntu at home from work.

-hendysg

---

