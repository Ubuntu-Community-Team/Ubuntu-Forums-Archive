---
title: "Memory Upgrade"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by ravi.786 on 2008-01-11
Hi everyone,
I have 1 GIG of RAM on my PC its a Dual core Processor, 
As i do not need any games or Video to play, I just need this system to Practise on application servers basically Weblogic, tomcat Jboss etc....
But 1 gig of memory is not sufficient, what all Files or software i can delete which will make my 1 Gig of memory more usable...

*Yes this Memory is not enough ok , I want to run weblogic 1 admin and managed server 768MB goes there with nodemanager, then Apache webserver Also Jmeter so here goes my all RAM*

---

### Post by Niniel on 2008-01-11
How's that not enough? Linux isn't overly memory hungry, so I would say 1 GB is plenty to run a server, even more so if you don't run a GUI on it. 
Deleting files won't help with your RAM though, for that you'll need to disable non-essential services and applications that run in the background.

---

### Post by Paul820 on 2008-01-11
What makes you think 1Gig of memory is not enough? I have 1Gig and i have never used all of it yet. I don't play games either but i have had many many applications open at the same time and have had no trouble at all. Deleting files or programs won't make any difference in memory being used until that application has been started. To save memory you can go through your startup programs and decide what you need or don't need from there, like bluetooth etc.

---

### Post by eolson on 2008-01-11
System > Administrations > System Monitor

    and watch your memory usage

alternate

Open a terminal, enter

    Top

and watch it on there.

I seriously doubt if you will ever use anywhere close to a Gig.

---

### Post by stchman on 2008-01-11
> **ravi.786 said:**
> Hi everyone,
I have 1 GIG of RAM on my PC its a Dual core Processor, 
As i do not need any games or Video to play, I just need this system to Practise on application servers basically Weblogic, tomcat Jboss etc....
But 1 gig of memory is not sufficient, what all Files or software i can delete which will make my 1 Gig of memory more usable...

I have 1G on my desktop and laptop and use less than 400MB worst case.

---

### Post by ravi.786 on 2008-01-11
> **Paul820 said:**
> What makes you think 1Gig of memory is not enough? I have 1Gig and i have never used all of it yet. I don't play games either but i have had many many applications open at the same time and have had no trouble at all. Deleting files or programs won't make any difference in memory being used until that application has been started. To save memory you can go through your startup programs and decide what you need or don't need from there, like bluetooth etc.


Yes this Memory is not enough ok , I want to run weblogic 1 admin and managed server 768MB goes there with nodemanager, then Apache webserver Also Jmeter so here goes my all RAM

---

### Post by Niniel on 2008-01-11
Then you'll have to install more physical RAM, nothing else will do.

But are you sure Weblogic is actually using 768 MB of RAM all the time? Don't forget, there is a swap partition where currently inactive code can be parked, freeing up physical RAM. 

Have you seen [this]("http://edocs.bea.com/wlibc/docs70/install/cvprerequisites.html#1031545")? 

> Hardware on UNIX

Your computer must have the following minimum configuration to successfully install WebLogic Integration - Business Connect on a UNIX platform.

    * Random Access Memory (RAM)

          o 256MB recommended

          o 128MB minimum 

    * 250MB available hard drive space (see note)

    * CD-ROM drive

    * TCP/IP network interface

    * A persistent Internet connection. 

Note: We recommend at least a 1 GB hard drive for both the application and the documents you exchange.

Or is that the wrong program?

---

### Post by Niniel on 2008-01-11
Here are the requirements for [Weblogic server]("http://e-docs.bea.com/wls/docs60/install/instpre.html#1043851"):

> System Requirements

The system requirements for WebLogic Server are given in the following table.

Component
	

Requirement

Platform
  	

A certified WebLogic Server platform. See the Platform Support page at [http://e-docs.bea.com/wls/certifications/certifications/index.html;](http://e-docs.bea.com/wls/certifications/certifications/index.html;) this page includes the recommended Java run-time environment versions and, when appropriate, other prerequisites or recommendations, such as operating system patches, kernel configuration values, and performance packs.

For more information about performance packs, see "Using WebLogic Server Performance Packs" in the Performance and Tuning Guide.
 

Hard disk drive
  	

For a WebLogic Server 6.0* installation on a Windows system-about 171 MB** of free storage space.

For a WebLogic Server 6.0* installation on a UNIX system-about 210 MB** of free storage space.

For a Service Pack installation on a Windows or UNIX system-about 149 MB*** of free storage space.
 

Memory
  	

For a Windows or UNIX system, 128 MB of RAM minimum (more may be required if you are running on a cluster).
 

Color bit depth display
  	

For graphical user interface (GUI) mode installation, 8-bit color depth (256 colors).

For console-mode and silent-mode installation, there is no color bit depth requirement.
 

  * With Service Pack already applied.

 ** Includes 76 MB of temporary storage space required by the installer program.

*** Includes 39 MB of temporary storage space required by the Service Pack installer program.

---

