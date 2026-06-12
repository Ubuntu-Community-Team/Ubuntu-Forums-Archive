---
title: "Networking issues with server"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by RobotMonkey on 2006-02-09
Hello everyone, I'm currently a Linux noob who's gotten himself in way over his head, and would greatly appreciate a helping hand.

What I'm trying to do is set up a headless web development server, accessible only from my home network, running Apache, and accessible through ftp and ssh.  Anyway, I was following an online tutorial ([this one]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10"), I believe, though I skipped the mail setup section), and got everything running as intended.  I also got sshd and ProFtpd working, making the box accessible from my Windows PC via FTP, SSH, and Firefox; and was quite pleased with the way things turn out.

Anyway, all was well until I powered down and restarted the computer.  Lacking any better ideas, I had set the hostname in /etc/hosts and /etc/hostname to their placeholder text, server1.example.com.  In retrospect, this appears to have been a bad idea :-| .

Anyway, upon bootup, I was greeted with an error message about being unable to resolve the FQDN.  Looking around, I set the host name back to ubuntu, in both /etc/hosts and /etc/hostname, powered down, and restarted the computer.  Now, I get a different error message:

/etc/init.d/rc:  line 30:  /etc/rc2.d/S50proftpd:  Permission denied

Trying things out anyway, the system is inaccessible over the network through FTP, SSH, and HTTP, though I can get in from the system itself ('ftp localhost', 'ssh localhost', 'lynx localhost').  I can also ping it at its IP address just fine.  I really don't know where to go from here, so I figured I'd ask for some help - What's going on here, what did I break, and how do I fix it?

Thanks in advance, guys!

/etc/hostname:
     ubuntu

/etc/hosts:
     127.0.0.1       localhost.localdomain     localhost     ubuntu

     # The following lines are desirable for IPv6 capable hosts
     ::1           ip6-localhost ip6-loopback
     fe00::0     ip6-localhost
     ff00::0     ip6-mcastprefix
     ff02::1     ip6-allnodes
     ff02::2     ip6-allrouters
     ff02::3     ip6-allhosts

---

