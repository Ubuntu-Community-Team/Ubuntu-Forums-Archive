---
title: "[Question]changing ip"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by shushustrum on 2007-08-09
Hi
is there any way in ubuntu u can change external ip.(because i want to download from rapid share)
is yes can someone please explain exactly how to do.iv been searching for days and cant find!
anthor question:can someone please give me some were i can learn how to use scp.i am new and dont know how to use it at all.
thanks!

---

### Post by Dr Small on 2007-08-09
You can not change your external IP address.
That is assigned to you by your ISP. If you want to mast it, use Tor.

Dr Small

---

### Post by shushustrum on 2007-08-09
what is Tor.?

---

### Post by Dr Small on 2007-08-09
[http://tor.eff.org/](http://tor.eff.org/)

Here is a page that explains how to set it up:
[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

Dr Small

---

### Post by splintercellguy on 2007-08-09
Tor is an anonymity network: [http://tor.eff.org](http://tor.eff.org) That said, the performance kinda sucks at the start.

---

### Post by Dr Small on 2007-08-09
I use Tor when I go on IRC and when I browse the web at times, and it is just slow, but it does it's job. Tor routes your internet through different onions (other people's internet) and then reaches the destination. Why of course your internet would be slow after passing through so many slow onions...

Dr Small

---

### Post by shushustrum on 2007-08-09
ok so i guess i can't change my external ip through ubuntu.
anthor question:how do i remote to my ubuntu through linux or windows.
the easiest way because i am new to linux.so i need a easy way to do it and ill understand how to do.
thanks

---

### Post by Dr Small on 2007-08-09
Could you please rephrase that question, as I am having trouble interpreting it.

---

### Post by Ek0nomik on 2007-08-09
Does Tor manage the onion servers?

---

### Post by Dr Small on 2007-08-09
I think tor just automatically routes through and randomly picks an onion(s) and then makes the connetion. Only in Windows with Vidilia could you manage and pick which onions you wished to connect through.

Dr Small

---

### Post by Ek0nomik on 2007-08-09
> **shushustrum said:**
> ok so i guess i can't change my external ip through ubuntu.
anthor question:how do i remote to my ubuntu through linux or windows.
the easiest way because i am new to linux.so i need a easy way to do it and ill understand how to do.
thanks

You want to access your Ubuntu computer via Linux or Windows remotely?

You can use SSH or you could use a Remote Desktop.

SSH:  [https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

Remote Desktop:  [http://ubuntuforums.org/showpost.php?p=2757451&postcount=6](http://ubuntuforums.org/showpost.php?p=2757451&postcount=6)

[http://ubuntuforums.org/showthread.php?t=515979](http://ubuntuforums.org/showthread.php?t=515979)

---

### Post by Ek0nomik on 2007-08-09
> **Dr Small said:**
> I think tor just automatically routes through and randomly picks an onion(s) and then makes the connetion. Only in Windows with Vidilia could you manage and pick which onions you wished to connect through.

Dr Small

Hm, this just seems really odd.  Who are running these onion servers?  Potentially you could be making yourself an easier target.  :lol:

---

### Post by Dr Small on 2007-08-09
[http://tor.eff.org/overview.html.en](http://tor.eff.org/overview.html.en)

---

### Post by shushustrum on 2007-08-09
what is the easiest way to remote to my computer?
and how can i do that?i am new to linux and don't understand in those stuf (yet:])

---

### Post by Dr Small on 2007-08-09
First, if you want to connect to your Ubuntu machine from a windows machine, you will need to install open-sshd (I believe is what it is called), and then get PuTTY to connect to your ubuntu machine from windows.


Dr Small

---

### Post by Ek0nomik on 2007-08-09
> **shushustrum said:**
> what is the easiest way to remote to my computer?
and how can i do that?i am new to linux and don't understand in those stuf (yet:])

SSH will allow you to use a shell (terminal or command line interface if you will) to control your computer.  You can also run programs over SSH.  If you are controling the computer using Linux on your local machine, you can open programs installed on the remote machine on the local one.  You can also do this in Windows, but you will need software to emulate the linux desktop environment.

If you want to control the computer in a totally visual manner (as most Windows users are used to, you move the mouse on the computer, what you type shows up on that computer etc) then you will want to look at the links I provided you with a few posts above that deal with Remote Desktop (also called VNC).

---

### Post by shushustrum on 2007-08-09
ya but thats what i said that i dont want you to tell me install this and that and then do it.
i have no clue what to do.what my machine name is?how i connect to it?what can i do when i connect truogh ssh.because it is command line right?
that's why i want exactly how to do it

---

### Post by Ek0nomik on 2007-08-09
> **shushustrum said:**
> ya but thats what i said that i dont want you to tell me install this and that and then do it.
i have no clue what to do.what my machine name is?how i connect to it?what can i do when i connect truogh ssh.because it is command line right?
that's why i want exactly how to do it

I am trying to figure out which method you are going to prefer, VNC (Remote Desktop) or SSH.  In my last post, which of the two methods sounds most appealing to you?

Once I know that, then I can help you with one or the either.  :)

---

### Post by Skidpad on 2007-08-09
> **shushustrum said:**
> Hi
is there any way in ubuntu u can change external ip.(because i want to download from rapid share)
is yes can someone please explain exactly how to do.iv been searching for days and cant find!
anthor question:can someone please give me some were i can learn how to use scp.i am new and dont know how to use it at all.
thanks!

If you are on a Static IP, you can't, but if your ISP issues IP addresses via DHCP, you probably can.  DHCP usually involves a pre-determined IP address lease time, but not always.  When I had dsl, I turned off my dsl modem when not using the computer.  When I turned it back on, it would authenticate with the ISP, and  then the ISP would issue a new WAN IP address.  I could do this every  minute, and would have a new WAN IP every time. 

I used this to my advantage to download from RapidShare - just unplug for a few seconds, and then download with my new IP.

You can check your current WAN IP via a number of websites, ipchicken.com, speedtest.net just to name two of them.  See what your IP is, and then experiment, or contact your ISP for more info.

---

### Post by shushustrum on 2007-08-09
> **Ek0nomik said:**
> I am trying to figure out which method you are going to prefer, VNC (Remote Desktop) or SSH.  In my last post, which of the two methods sounds most appealing to you?

Once I know that, then I can help you with one or the either.  :)
does x11vnc show you your desktop in graphics?
and if i use ssh can i open a site and do stuff there on my computer?for example or transfer songs to my ipod?
what do you recommend?remember im new to linux and not that good at doing my stuff with command line.
do you have an AIM/ICQ/MSN messenger?so i can talk to u live?

---

### Post by Ek0nomik on 2007-08-09
> **shushustrum said:**
> does x11vnc show you your desktop in graphics?
and if i use ssh can i open a site and do stuff there on my computer?for example or transfer songs to my ipod?
what do you recommend?remember im new to linux and not that good at doing my stuff with command line.
do you have an AIM/ICQ/MSN messenger?so i can talk to u live?

I do have AIM, ICQ, and MSN.  You can see it in my Ubuntu Forums profile or even on this post.  AIM is my preferred client, btw.

If you use VNC, you essentially are seeing the monitor of your remote computer, on your local one.  It's a, "what you see if what you get" sort of deal.  An exact replica of your remote computer's desktop.

So, if you are looking for that, then you want to use VNC.

If you want to transfer songs, you will want to use SSH.

So, I think VNC is pretty self explanatory, and I imagine you understand what that is now.

Let me explain SSH briefly...

With SSH, you can have a terminal that controls a remote computer, instead of your own.  I think you can figure out what that means.  Basically imagine your current terminal, but everything you do in it happens on the remote computer.  Now, you can also open programs with SSH from the remote computer.

Let Computer A = Local Computer
Let Computer B = Remote Computer

Let's say I have Bluefish (an HTML editor) installed on my remote computer.  If I log into the remote computer via SSH on Computer A, I can type: 'bluefish' and the Bluefish program will load.  **Any and all** files I make while using this program are actually saved on Computer B, the remote computer.  I can even run Bluefish if I **don't** have it installed on Computer A.

This is a really powerful and, in my opinion, awesome feature of SSH.

Maybe you should just try them both out.  SSH is *really* easy to get working.

Is your remote computer going to be running Windows or Linux?

If you have more questions just reply in the thread.  I'd prefer to discuss in this thread as it may help people in the future, as opposed to our AIM conversation.  :)

---

### Post by shushustrum on 2007-08-09
the local computer is windows. i think ill try them both ill try the easyer one first wich will that be?and how do i do it?from the beginning how to install and how to use.sorry im just new

---

### Post by Ek0nomik on 2007-08-10
> **shushustrum said:**
> the local computer is windows. i think ill try them both ill try the easyer one first wich will that be?and how do i do it?from the beginning how to install and how to use.sorry im just new

So, did you get your ports forwarded correctly so you could SSH into the box?

---

