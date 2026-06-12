---
title: "New to linux and want to set network file share"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by twbdan on 2007-10-23
I am new to Linux, I am a school principle and I want to set up user accounts for my students and staff.
I have one dedicated box to serve as a server.  I installed 7.10 on this machine.  I also have 25 computers that have xp pro on them.  Each machine is set up under the user group called WORKGROUP and each machine have their individual name (dan01, dan02...).  The machines are setup in pods in all our classrooms.  Each classroom has one hp printer that is already shared using the print share in XP.  I basically want to setup file shring so that student can retrieve their work from any work station, allow student to dump their finished work in a folder that can be accessed by my teaching. 

A folder on my desktop allows me to see all the computers in our system.  I have been able to open files that I put into the file share under XP
thanks for your help

Daniel

---

### Post by p_quarles on 2007-10-27
What you're looking for is a Samba domain controller. There's a decent tutorial here:
[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

It's for a slightly older version of Ubuntu, but most everything should be the same. I do understand that the 7.10 server edition has some new configuration options during installation, but that would be the main difference. You can also just ignore the instructions for setting up printer sharing, since you've already got that covered. 

Like I said, this is a decent tutorial, but I'm suggesting it more to point you in the direction of a solution rather than to suggest that this is all you'll need. Since you'll be deploying this server in an important role, I would suggest trying to find a good Samba manual. I believe O'Reilly publishes such a book, and I've had very good luck with their publications.

---

