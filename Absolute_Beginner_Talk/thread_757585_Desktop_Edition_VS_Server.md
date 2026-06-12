---
title: "Desktop Edition VS Server"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by jessmagz on 2008-04-17
Hi everyone!

Im new to ubuntu linux. I just installed ubuntu 7.10 last week and today I upgraded to 8.04 LTS (but till now, not completed). These are my questions, please enlighten me on the following. Thanks in advance!

   1. I'm sure my upgrade now will not be completed until 5pm today. But it's almost 30% done in "getting new packages". Can i just continue this tomorrow without losing the files just downloaded today?
   
   2. Im using a 64bit PC with 1Gig of RAM. but i notice that the system is not too fast comapred to my old Fedora Core 6 (running on P4 PC with 512MD RAM). How do i know the default programs, services or daemons between a server and a desktop edition of ubuntu? I ask this because I'll be actually using my ubuntu box as a webserver but i dont know much of the commands in UNIX so I decided to install a Desktop edition. Can anyone help me with this? I just want to know which program or services or daemons should I keep so that I can eliminate the rest...

Thanks!

Best regards,
Jess

---

### Post by martrn on 2008-04-17
There really is not that much diffrence between the server edition and the desktop edition.  With the desktop edition it installs gnome and the Xwindows system and some deskop applications.  With the server edition is installs a terminal, no X-windows system and apache, php, and prostegueSQL, and a whole host of email demaons, dovecott, imap login, poplogin, and postix mail servers etc.

The server edition is a pretty light system, and brillient even for installing a desktop system, its a simple matter of installing a desktop and configuring the Xserver properly.  If installing a desktop system to run as a server you would only need to install apache, php, and your mail and SQL servers and in would be the same as installing the server version and a desktop.

There really is not much diffrence between installing a desktop system + apache/php/mysql or a server system + gnome desktop, other than I personally find it eaiser to install the server version, and I guess you and other find it easier to install a desktop version.

---

### Post by jessmagz on 2008-04-17
thanks bro!

I really appreciate your immediate and informative reply! 
Well, as you said, I have to set of install options. 
   1. Desktop Edition + server utilities like apache, php, sql, and mail.
       Well in my case, that's what I did. I installed Drupal-5.3 using apt-get, also with   
       apache2, php and MySQL. But as I noticed, using the Synaptic Package Manager, I 
       have had a lot of programs install which I actually don't know what their uses are. 
       That's why I'm thinking if it is advisable if I'll overwrite my Desktop install with a Server  
       install then just add GNOME?
   2. Server Install + GNOME.

Thanks a lot bro!

Best regards,
Jess

---

### Post by hyper_ch on 2008-04-17
main difference: Wit the desktop/alternate cd you get a "desktop" ready comuter with email, office, browser, multiemdia programs installed.

With the server you will install a minimal system and a kernel optimized for server (headless) tasks...

---

### Post by martrn on 2008-04-17
If you install Server Ubuntu + Xwindows + Gnome
or if you install Destop Ububntu + php +mySQL + prostegeSQL + apache + mail 

I think in thoeory you will have exactly the same system.

I installed the server system and added Xwindows + Kubuntu, and have demons running that I am not terriable clear about.

If your system is running a little sluggishor you need to optimise you system for your particular requirements then install sysv-rc-conf

```
sudo apt-get update
sudo apt-get install sysv-rc-conf
```

and optimise your system by removing components you do not need.

The following sites have more information about these services I have running
[www.extremetech.com/article2/0,1697,2114124,00.asp]("www.extremetech.com/article2/0,1697,2114124,00.asp")
[http://blog.kutakutik.or.id/linux/tu...kubuntuubuntu/]("http://blog.kutakutik.or.id/linux/tu...kubuntuubuntu/")
or google [sysv-rc-conf ubuntu faster boot times]("http://www.google.co.uk/search?hl=en&as_q=sysv-rc-conf+ubuntu+faster+boot+times&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images") to find out how to optimise.

If you are developing either php progs or websites, you need more memoary in your system than an advridge user.
:)

---

### Post by zvacet on 2008-04-17
@** jessmagz**


> I'm sure my upgrade now will not be completed until 5pm today. But it's almost 30% done in "getting new packages". Can i just continue this tomorrow without losing the files just downloaded today?

No,but you know it now.You could install server on your desktop version by going to the** synaptic>edit tab>mark packages by task>LAMP**.

---

