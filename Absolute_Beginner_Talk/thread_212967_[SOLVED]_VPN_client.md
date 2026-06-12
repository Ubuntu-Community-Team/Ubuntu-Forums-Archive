---
title: "[SOLVED] VPN client"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by mustbealennox on 2006-07-10
Hello,

I would like to ditch Windoze and upgrade to Linux. A friend recommended ubuntu, so here I am. :-)

I have to run a VPN client for work, but the download page indicates that the most recent version is supported for these Linux distributions:

    * Added support for Linux Fedora Core 3 and Fedora Core 4.
    * Added support for Linux SuSe 9.2 and 9.3.
    * Added support for Linux RedHat Advanced Server 4.

For these types of applications, is it normally a requirement to install a specific Linux distribution, or is the kernel version the only real requirement? If the latter, then which versions of the kernel come with 5.10 and 6.06? I wasn't able to find it in the documentation.

In general, I'm unsure of how the kernel version is (de)coupled to/from the distribution. Is it possible to change kernel versions?

Thanks!

---

### Post by steve.horsley on 2006-07-10
You should always look in synaptic to see if the software you want is already in the Ubuntu repositories before downloading from elsewhere - it's so much easier. In this case, the package name is probably pptp-linux which is in the standard repo.

After installing, you will find docs in /usr/share/doc/pptp-linux, but I found better instructions by googling. Good luck.

---

### Post by mustbealennox on 2006-07-10
Thanks for your reply.

From what I understand, I can't log into work unless I'm running the VPN client provided by my company. I don't think pptp-linux is an option.

I dug around a bit more, and found further Linux requirements:
Linux 2.2.x or 2.4.x kernels, RedHat 7.0 – 9.0, Advanced Server, Enterprise Server, SuSE 8.2 – 9.x (client will only work on Intel-based Linux system)

I'm willing to install Ubuntu and give it a try, but I'd like to know which kernel version comes with 5.10. Where in the documentation is this mentioned?

Thanks again,
Ben

---

### Post by steve.horsley on 2006-07-11
Not sure where the version is mentioned, but all versions of Ubuntu come with a kernel version 2.6.x. Also, version 6.06 is the latest version of Ubuntu.

It would help if you could find out who's VPN client it is - i doubt they wrote their own. Have you used the Windows version? Does it splash up a manufacturer's logo?

---

### Post by mustbealennox on 2006-07-12
The VPN Client is supplied by Apani ([www.apani.com)](www.apani.com)).

I work for Nortel, and use their Contivity VPN Client for remote access to work.

I assumed that 6.06 would be running a later kernel (had the same problem when looking into Fedore Core 5), and hoped that 5.10 would be running 2.4.x. I would have been willing to install an older release of Ubuntu until Apani supplies a newer version of the VPN Client with support for the 2.6.x kernel.

Are there other options for me (regarding VPN clients and/or Ubuntu distributions)?

Cheers,
Ben

---

### Post by cwaldbieser on 2006-07-12
> **mustbealennox said:**
> The VPN Client is supplied by Apani ([www.apani.com)](www.apani.com)).

I work for Nortel, and use their Contivity VPN Client for remote access to work.

I assumed that 6.06 would be running a later kernel (had the same problem when looking into Fedore Core 5), and hoped that 5.10 would be running 2.4.x. I would have been willing to install an older release of Ubuntu until Apani supplies a newer version of the VPN Client with support for the 2.6.x kernel.

Are there other options for me (regarding VPN clients and/or Ubuntu distributions)?

Cheers,
Ben

What kind of VPN server are you connecting to?

---

### Post by mustbealennox on 2006-07-12
> **cwaldbieser said:**
> What kind of VPN server are you connecting to?

We connect to a Nortel VPN box. I'm unsure of the actual model number, but could query our IS department if that makes a difference.

A Linux savvy colleague of mine sent me a couple of links regarding an attempt by Openswan to connect to the Nortel VPN server as a client:
[http://wiki.openswan.org/index.php/Nortel%20Contivity](http://wiki.openswan.org/index.php/Nortel%20Contivity)
[http://lists.openswan.org/pipermail/users/2004-September/002391.html](http://lists.openswan.org/pipermail/users/2004-September/002391.html)

Seems like I may be out of luck without a 2.4.x kernel.

Cheers,
Ben

---

### Post by madsaientist on 2006-07-21
I was just checking out the Openswan site and they have a version that works with the 2.6 kernel.  The link they have on the site is to an rpm but you could convert it using alien.  Oh, and I just checked the repositories and it's listed in there as well.  I think it's best that you get it from the repository.

Here is the link to the Openswan site: [http://www.openswan.org/code/](http://www.openswan.org/code/)

If you try it let me know if it works.  I'm having a problem finding a client to use as well.

---

### Post by WrathofthePenguin on 2006-08-09
> **mustbealennox said:**
> We connect to a Nortel VPN box. I'm unsure of the actual model number, but could query our IS department if that makes a difference.

A Linux savvy colleague of mine sent me a couple of links regarding an attempt by Openswan to connect to the Nortel VPN server as a client:
[http://wiki.openswan.org/index.php/Nortel%20Contivity](http://wiki.openswan.org/index.php/Nortel%20Contivity)
[http://lists.openswan.org/pipermail/users/2004-September/002391.html](http://lists.openswan.org/pipermail/users/2004-September/002391.html)

Seems like I may be out of luck without a 2.4.x kernel.

Cheers,
Ben

Hi Ben -

The model number of the Contivity won't make a difference for what you're trying to do (There are only a couple of models that don't allow user tunnels and Nortel doesn't use them for employee connections). What will make a difference is that Nortel requires you to use the Nortel VPN client. There isn't a way around this - it's an option for the Contivity that they've enabled.

---

### Post by mustbealennox on 2006-08-10
> **WrathofthePenguin said:**
> Hi Ben -

The model number of the Contivity won't make a difference for what you're trying to do (There are only a couple of models that don't allow user tunnels and Nortel doesn't use them for employee connections). What will make a difference is that Nortel requires you to use the Nortel VPN client. There isn't a way around this - it's an option for the Contivity that they've enabled.

Thanks for the information. Looks like that answers all of my questions. Once we're provided with a 2.6 compatible VPN client, I'll look into installing Ubuntu on my system at home.

---

### Post by mustbealennox on 2007-11-19
For any other Nortel employees wondering how to connect to work from a Ubuntu-based PC, just search for "CVC Client on Ubuntu" on the intranet and you'll find instructions.

---

