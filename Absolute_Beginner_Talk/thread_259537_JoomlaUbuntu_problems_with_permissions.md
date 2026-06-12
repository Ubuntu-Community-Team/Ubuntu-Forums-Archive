---
title: "Joomla/Ubuntu problems with permissions"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Paradoxed on 2006-09-17
Good day all from a swelllering Vietnam,
[U]
The problem:[/U] After installing php/mysql/apache I downloaded Joomla. I created a dir under /var/www/joomla. So far so good (apache etc running) However the joomla package I downloaded is a tar.gz file. I can extract the files to the desktop via Archive Manager, but I need to extract it to /var/www/joomla

First Problem
When I use Archive Manager and point it to the location to extract to the following 

"Extraction not performed

You don't have the right permissions to extract archives in the folder "/var/www/joomla""

When I type the command  tar -zxvf    Joomla_1.1.0.11-Stable-Full_Package.tar.gz 

I also tried -xvjf............

I get the followng
tar: Joomla_1.1.0.11-Stable-Full_Package.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

(is there something that must prefix the command to point to the desktop perhaps?)


Question 1: What would the command line entry be to extract this to the destination I want? (/var/www/joomla)

I tried the following

sudo mv Joomla_1.0.11-Stable-Full_Package.tar.gz_FILES  /var/www/joomla
mv: cannot stat `Joomla_1.0.11-Stable-Full_Package.tar.gz_FILES': No such file o r directory

Any help appreciated

---

### Post by Perfect Storm on 2006-09-17
Extract the package

cd /into/extracted/package
sudo cp -r * /var/www/joomla (if the joomlar folder is made)

other wise make the folder fist
cd /var/www
sudo mkdir joomla

---

### Post by Paradoxed on 2006-09-17
Unreal response time! Thanks for that.

Okay the package is extracted to my desktop. 

And the filename is now 
Joomla_1.0.11-Stable-Full_Package.tar.gz_FILES

Now if you do not mind: how do I move this folder to /var/www/joomla

(the directory does exist)

---

### Post by ChadMMc on 2006-09-17
To copy to the /var you have to be in supervisor mode (sudo in front of each command for changing things there)

hope this helps a little.

---

### Post by Perfect Storm on 2006-09-17
Well, I missunderstood something in your thread /my fault
Back to the tar file

sudo tar -zxf Joomla_1.1.0.11-Stable-Full_Package.tar.gz  /var/www/joomla

---

### Post by Paradoxed on 2006-09-17
Again thank you so mu. The thing is that I have no idea what the command would be to move these files. What is it that I must type to "move file" and what must I type to point the move to /var/www/joomla.

I am busy researching as much as I can.I have been struggling for the past two days and thought I would ask here.

Thank you for being patient

---

### Post by Perfect Storm on 2006-09-17
Well, the command I just show you move the compressed files to <location>

I good idea is to
```
man mv

```

or

```

mv --help
```
for more information

If it's a move command you are looking for.

---

### Post by Paradoxed on 2006-09-17
> **Artificial Intelligence said:**
> Well, I missunderstood something in your thread /my fault
Back to the tar file

sudo tar -zxf Joomla_1.1.0.11-Stable-Full_Package.tar.gz  /var/www/joomla

Logged in as root 


root@dhcppc0:/home/steve# sudo tar -zxf Joomla_1.1.0.11-Stable-Full_Package.tar.gz /var/www/joomla
tar: Joomla_1.1.0.11-Stable-Full_Package.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /var/www/joomla: Not found in archive
tar: Error exit delayed from previous errors
root@dhcppc0:/home/steve#

---

### Post by Perfect Storm on 2006-09-17
```
sudo tar -zxvf Joomla_1.1.0.11-Stable-Full_Package.tar.gz -C /var/www/joomla



```


Sorry...diffently need sleep :-/

---

### Post by Paradoxed on 2006-09-17
No worries. Get some sleep. Its almost 3am here. 

This the message again

tar: Joomla_1.1.0.11-Stable-Full_Package.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Perfect Storm on 2006-09-17
Are you sure you are in the right directory?

---

### Post by Paradoxed on 2006-09-17
=D> 

Aaaaah. I use sudo nautilus and simply dragged the files into the directory that I wanted it. It all works now!!

---

### Post by Perfect Storm on 2006-09-17
Good, you got it working :)


Time for sleep, have to get to work in 7 hours.

---

### Post by Paradoxed on 2006-09-18
Alright so now after downloading Joomla, I have the follwing problem.

On the first step of installation there are two areas in red.

- MySQL support  	 Unavailable
configuration.php 	Unwriteable

Anyone know how I can sort this out?

---

### Post by bluefrog on 2006-09-18
need to chown (man chown) to www-data your joomla directory

sudo chown -R www-data /var/www/joomla

James

---

### Post by Paradoxed on 2006-09-18
James thanks a lot!'

sudo chown -R www-data /var/www/joomla sorted out the php problem


But still have an issue with

- MySQL support  	 Unavailable

---

### Post by bluefrog on 2006-09-18
Silly question... Have you installed mysql server? (4 or 5 doesn't matter..)

James

---

### Post by Blix11 on 2006-09-20
I have that exact problem with the MYSQL support thing. And I know I installed mysql-server. Can you tell me how to solve this problem?

---

