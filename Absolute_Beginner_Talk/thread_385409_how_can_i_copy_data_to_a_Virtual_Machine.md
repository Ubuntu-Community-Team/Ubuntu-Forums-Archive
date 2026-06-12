---
title: "how can i copy data to a Virtual Machine?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-03-15
Hi
I have just set up XP in VM Server and am very impressed!!:KS 

I Need XP to run google Sketchup And i Want to transfer my old plans to the Virtual drive system.
Can anyone help please?

Thanks

Mike

---

### Post by lamalex on 2007-03-15
the only way ive found is via ssh and scp. if youre doing large files use rsync.

---

### Post by MrKlean on 2007-03-15
Never used either program, but I would save them to cd....then you have them forever.. then just read them off the cd into VM.... a thot ; )

---

### Post by qpwoeiruty on 2007-03-15
VMWare has support for transferring between host and guest. I'm not sure if it's in Server, I'm using the Workstation Beta. Before that, with player, I had to set up a share in Ubuntu (Samba). You could also burn a CD/DVD or make a CD image and mount it in VMWare. Another way is to put it on your USB flash drive.

---

### Post by lamalex on 2007-03-15
> **qpwoeiruty said:**
> VMWare has support for transferring between host and guest. I'm not sure if it's in Server, I'm using the Workstation Beta. Before that, with player, I had to set up a share in Ubuntu (Samba). You could also burn a CD/DVD or make a CD image and mount it in VMWare. Another way is to put it on your USB flash drive.

vmware server does not support sharing, easiest is to scp files back and forth. if you don't know how to scp, here is how
```

scp [file you want to send] root@ip.of.receiving.client:/path/to/file
i.e.
scp ironmaiden-headforthehills.mp3 root@192.168.0.100:/home/thebeast/music

```

* is a wild card, so if you want to send every mp3 do *.mp3

---

### Post by mpooley on 2007-03-15
Thank you
I've tried using the usb drive as this sounded the easiest but the Windows VM does not see it?

as for scp I'm using nat so what would my ip address be and how would i find it :confused: 
sorry for being so ignorant!

If all else fails i'll go the CD route but would like an easier way to do this as i can see this being needed again.

Mike

---

### Post by AndyCooll on 2007-03-15
> **Iamalex said:**
> vmware server does not support sharing, easiest is to scp files back and forth. if you don't know how to scp, here is how

This is incorrect. VMware Server **does** support sharing. I have Samba installed on my Server and have the same share access to my home drive and other shared folders with my XP image as I do with my other Linux boxes.

:cool:

---

### Post by ghstridr on 2007-03-16
> **AndyCooll said:**
> This is incorrect. VMware Server **does** support sharing. I have Samba installed on my Server and have the same share access to my home drive and other shared folders with my XP image as I do with my other Linux boxes.

:cool:

Actually, you read his post incorrectly.  He is right, VMware Server does 'not' support sharing via any mechanism internal to itself (referring to the vmware server process).  You are accomplishing sharing by using network based protocols (smb in this case) to transfer files around.  Now you may have Samba installed on the same box as the VMware Server, but that is not the same as being able to transfer data directly between two machines via a mechanism supplied by VMware.

---

### Post by lamalex on 2007-03-16
yeah sharing via samba would be pretty much the same as sharing via scp, a bit more efficient depending how you set stuff up.

as for your ip, in your windows box type ipconfig in a command prompt, that will tell you your ip.

---

### Post by luckylucky on 2007-03-16
I have several ways I share files back & forth between Ubuntu & Winblows inside and outside of VMware.  For limited occasional file transfers a USB sneakernet is certainly easy, but what I like to do is I have a Win2000 VMware and on the desktop I've simply created a network shared folder.  This is easily accessible within Ubuntu by going to "Places" > "Network Servers" and it is there.  Once I enter my Winblows user&login info I have unrestricted access to move files in both directions.

Hope this helped!

Ubuntu Rocks!!! :guitar:

---

### Post by mpooley on 2007-03-17
> **luckylucky said:**
> I have several ways I share files back & forth between Ubuntu & Winblows inside and outside of VMware.  For limited occasional file transfers a USB sneakernet is certainly easy, but what I like to do is I have a Win2000 VMware and on the desktop I've simply created a network shared folder.  This is easily accessible within Ubuntu by going to "Places" > "Network Servers" and it is there.  Once I enter my Winblows user&login info I have unrestricted access to move files in both directions.

Hope this helped!

Ubuntu Rocks!!! :guitar:

Hi
sorry to be a pain but i cant see how to set up the shared folder in windows:confused: 
\i seem to need to run the network wizard on bvoth machines ? is this right?
my Virtual windows has a coonection to the internet but hell i'm just confused  LOL

Mike

---

### Post by mpooley on 2007-03-18
I have now run the setup wizard in windows xp and can now see my win connection in ubuntu.
I have created shared folders in windows but i am getting this message when i try to open the network connection
"Sorry, couldn't display all the contents of "Windows Network: mike-windows"."

could someone help me please:KS 

thanks

Mike

---

### Post by .simon on 2007-03-22
> **luckylucky said:**
> I have several ways I share files back & forth between Ubuntu & Winblows inside and outside of VMware.  For limited occasional file transfers a USB sneakernet is certainly easy, but what I like to do is I have a Win2000 VMware and on the desktop I've simply created a network shared folder.  This is easily accessible within Ubuntu by going to "Places" > "Network Servers" and it is there.  Once I enter my Winblows user&login info I have unrestricted access to move files in both directions.

Hope this helped!

Ubuntu Rocks!!! :guitar:


Hi there,

Could you expand on this please? I've been trying to set-up a shared folder and USB for some time now and am failing miserably...!

Thanks

Simon

---

### Post by thelinuxguy on 2007-03-22
> **mpooley said:**
> 
I have created shared folders in windows but i am getting this message when i try to open the network connection
"Sorry, couldn't display all the contents of "Windows Network: mike-windows"."


The shared folders thing worked for me. I did not have to run the Network Setup Wizard. Within Windows, right click on folder >> Sharing and Security >> Share this folder on the network. And then I could access it from ubuntu using System >> Network Servers.

However if this does not work for you, an alternative is to setup FTP sharing on the linux box. Details can be found here: [http://ubuntuforums.org/showpost.php?p=2331626&postcount=6](http://ubuntuforums.org/showpost.php?p=2331626&postcount=6)

This is an edgy answer ;-) (Referring to my post in your thread at [http://ubuntuforums.org/showpost.php?p=2327779&postcount=10](http://ubuntuforums.org/showpost.php?p=2327779&postcount=10))

---

