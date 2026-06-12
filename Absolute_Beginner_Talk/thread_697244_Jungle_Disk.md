---
title: "Jungle Disk"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-02-14
I am wanting to do some online backup with jungledisk, wondering if anyone is familiar with it. Can I install it on ubuntu 64bit, and if so how do i go about doing so

---

### Post by neurostu on 2008-02-15
I haven't heard of jungle disk. My recommendatin would be to download it then install it. If it works it works, if it doesn't contact Amazon support.

---

### Post by CodeWraith on 2008-02-16
I just set up JungleDisk today, and it's working great. I'm not on 64-bit but these are the steps I went through:

1. Sign up with Amazon Simple Storage ([http://aws.amazon.com/s3](http://aws.amazon.com/s3))

2. Follow the instructions to get the Access Key ID and Secret Access Key

3. Download the Linux version of JungleDisk ([http://www.jungledisk.com](http://www.jungledisk.com))

4. Extract the files to the home directory. It will make a directory called "jungledisk"

5. Double-click on "junglediskmonitor" and a configuration page will open

6. Enter the Amazon Access Key ID and Secret Access Key and leave Bucket Name as "default"

7. Go to Start > Places > Connect to Server... and add the following:

Server type: WebDAV (HTTP)
Server: localhost
Port: 2667
Name to use for this connection: whatever name you want displayed in Nautilus

8. Open Nautilus, find the drive, and double-click to open

9. It should now function like an extra drive with ability to copy, paste, and delete. Keep in mind that JungleDisk has to be running (there will be an icon in the tray) whenever you want to access the drive.

And there's lots more options in the INSTALLfile.

Cheers.

---

### Post by anderskitson on 2008-02-25
Awesome It works Great in 64bit, just got it today, great price and very easy to setup

---

### Post by olavjunior on 2008-03-02
I really HATE jungle disk! Just paid and everything, but nothings working! It won't use my secret keys, telling me there's something wrong with them when I try web access , and can't get the configuration to connect to my account telling me I haven't paid (wich I have)

I think it's a totally piece of ****!... I'm gonna buy space from some hosting service and use encrypted duplicity instead. Anybody who knows a good and fast one?

---

