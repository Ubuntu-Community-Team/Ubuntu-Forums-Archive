---
title: "Web Login"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by lalit on 2006-08-04
I need a small program [made by this company]("http://24online.elitecore.com/") for me to accesses my net. So i downloaded the Linux version from my ISP. It shows as a executable file but when i click nothing happens, thought the file was corrupt & downloaded again & still the same thing. Any answers ?

---

### Post by %hMa@?b&lt;C on 2006-08-04
you may have to run it from terminal
drag it and drop it into terminal, then press enter.

---

### Post by benuski on 2006-08-04
If its a windows exe file, you may need to download WINE and run it under that.  You'd have to download that from the repositories, and then right click on the file and click on Open with Wine, or something like that.

---

### Post by ytrium on 2006-08-04
The only thing relevent I could find was this, found at [http://gnowledge.org/pipermail/linuxers/Week-of-Mon-20030113/034394.html](http://gnowledge.org/pipermail/linuxers/Week-of-Mon-20030113/034394.html).

It's a long shot, but maybe it will help.  Good luck!

> ILUG-BOM] [LIH]Are you a cyberoam 24online user? (fwd)
romijain at antispam romijain@[EMAIL-PROTECTED] 
Tue Jan 14 20:11:29 IST 2003 

Previous message: [ILUG-BOM] RH8.0 Cds 
Next message: [ILUG-BOM] Meeting location 
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ] 

--------------------------------------------------------------------------------

Quoting  :
hi
i am using 24online client for last 2 years and not having any problems.even the client which i downloaded from sourceforge.net did not had any installation steps to be performed,just copy the file to /root folder and change file permissions...that it.run the client and login.
> 
> function SetDomain(d) { document.domain = d; }hey guys......
> 
> I am still struggling with 24online Client and Cyberoam on Linux...
> 
> I tried installing 24 Online CLient and Cyberoam using the Steps given
> by Vivek......That document was very well written..Even a dumb like me
> was able to follow all those steps properly......but at end.....it wasnt
> fruitful :(((
> 
> When i give ps -a | grep 24 Online 
> 
> I am also able to ping my CableNet Server......
> 
> It shows me the process is running.........but in log file i just
> see......\"start|stop\"
> 
> And am not able to Connect to any of the Sites:((((
> 
> Is there any wayr out?
> 
> Dont wanna use Windows for Internet:((
> 
>  
> 
>  
> 
>  q u a s i <quasiabhi at softhome.net> wrote:> 1. I wanted to know how many
> of the folks around here are using 
> > cyberoam 24online based cable networks. 
> 
> My cable-internet wallah uses 24online.
> 
> > 2. If you have, what have been your experiences with using it on
> > Linux.
> > a. Have you asked your cable network wallah about using the network
> > with Linux clients?
> 
> my cable wallah is \"huh? Linux? Boss apne ko to pata nahi hain!\"
> 
> > b. Or, have you given up and decided to use the windows machine for
> > accessing the Net
> 
> Nope. there is a wonderfull piece of work called linc
> linc.sourceforge.net
> To use it I had to make one minor change in the source code. That\'s all.
> In fact I am writing this mail on a linux box via 24online ! :-)
> 
> > 3. Are you still interested in finding out a way of using these
> > networks using Linux?
> 
> already have !! :D
> 
> cheers,
> quasi
> 
> 
> 
> _______________________________________________
> http://mm.ilug-bom.org.in/mailman/listinfo/linuxers
> 
> Catch all the cricket action. Download Yahoo! Score tracker

-------------------------------------------------
Sify Mail - now with Anti-virus protection powered by Trend Micro, USA.
Know more at http://mail.sify.com

Sunny`s column,World Cup Schedule, Scorecards, The cricket Store and much much more!!
http://www.khel.com/worldcup/

---

### Post by lalit on 2006-08-05
Tryed linc.sourceforge.net but nothing seems to work from there too .Anything else i can try ? I need to get that [24online client ]("http://24online.elitecore.com/")installed to get my internet connection going.

---

### Post by elijahclarity on 2006-10-18
Hi lalit.....I'm also facing the same prob. Linc should solve your problem if you set it up correctly. Its the open-source alternative to 24online client. I  will let you know if I get online with it successfully:)

---

### Post by bswilson on 2006-10-18
> **lalit said:**
> I need a small program [made by this company]("http://24online.elitecore.com/") for me to accesses my net. So i downloaded the Linux version from my ISP. It shows as a executable file but when i click nothing happens, thought the file was corrupt & downloaded again & still the same thing. Any answers ?

I just helped someone with this.  Apparently there's a open source alternative to this program, called **linc**.

[http://linc.sourceforge.net/](http://linc.sourceforge.net/)

---

### Post by goki75 on 2006-10-28
Cyberoam Client for Linux does not come in a executable format like in Windows. But as a zipped file (called a tar ball).

You need to download the client tarball. Put it in a folder.

The Client is available temporarily from this address

[http://www.mhowlinux.org/pub/CyberoamLinuxClient.tar.gz]("http://www.mhowlinux.org/pub/CyberoamLinuxClient.tar.gz")

And goto the console or shell (command prompt). Change directory to that folder and unzip the file by giving command

$ tar -zxvf CyberoamLinuxClient.tar.gz

After you unzip it enter the new directory created for Cyberoam Client by the unzipper(tar) and run the Cyberoam Client

$ ./crclient -s


enter the necessary parameters for you isp
and

to login 

enter

$ ./crclient -u <username>


Remember you need to be super user to do all this in ubuntu

to become super user
enter

$ su
Password:<enter the root password>

The Cyberoam Client is also attached to this post



Just found a more detailed escription

[http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20020408/004615.html](http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20020408/004615.html)

---

