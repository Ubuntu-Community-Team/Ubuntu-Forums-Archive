---
title: "VNC Viewer 4.2.6 Help"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by towersoft on 2006-08-31
Hi,
    I am trying to use the Binary file from realvnc so that I can connect to the enterprise edition of VNC as all the the packages I can get from synaptics do not support the security. I am just unable to get the Binary to run. I have put it in my home folder but I get the error "Couldn't display "/home/administrator/vnc-E4_2_6-x86_linux_viewer". Any help would be greatly appreciated as I am new to linux and am trying my best to get used to it :) I am running ubuntu on my Dell Latitude D410. Thanks again!.

Phil

---

### Post by jpeddicord on 2006-08-31
Right click on the binary file, and select Properties. Click on the Permissions tab. Next to User, there should be three checkboxes (read, write, execute). Make sure all three are checked. Close the window, and now you should be able to run the file. Run it in the terminal if nothing happens when clicking on it.

---

### Post by Toxicity999 on 2006-08-31
If it's an installer of some sort execute it in a su environment or it would probably fail. 

If you happen to have issues launching it graphically cd to that dir and type ./yourprogramnamehere

Might want to rename it to something simpler if it doesn't break anything... my fingers hurt just looking at it!

Edit: 300 posts... Not that it matters just interesting. Most of them have been responses in the Nubgard forum :KS

---

### Post by towersoft on 2006-09-01
Hi,
    I have tried your suggestions but nothing seems to work. Any other ideas ? :)

---

### Post by Toxicity999 on 2006-09-01
Start a new terminal environment and try

cd /home/administrator/
./vnc-E4_2_6-x86_linux_viewer

What errors does that produce?
If that doesnt work maybe it's some kind of fancy installer scripts all these windows companies do when they startup with linux.

If thats the case (For this you need to set a root password!)
try

su
enteryourrootpassword
cd /home/administrator/
./vnc-E4_2_6-x86_linux_viewer

I'll spend a few minutes goin to htere site and try to learn some mroe for you I'm just shooting in the darks with what ifs till I read around there.

---

### Post by Toxicity999 on 2006-09-01
Blah I poked around the Site (RealVNC right?) I got the free version but it's not at all like what you got. vnc-4_1_2-x86_linux.tar.gz I you sure you aren't trying to open the Tar file as a binary? Maybe some how the .tar.gz got trimmed but man... the names look VERY similiar. Just the free version is a little back there apparently.

I don't know like I said I'm just trying to help on no real knowledge founding, I'm speaking in generalities, I don't have much experience but no one else has poked in so for now I guess my bad advice is all there is =P

---

### Post by towersoft on 2006-09-01
Thanks for your help m8 it is really apreciated. I was just trying to run the enterprise viewer as it uses higher security. I have downloaded the full package and it contains a JAVA client which works when I run the index.vnc. Ok all well and good but I would like to run it from my applications menu. I have gone through alacarte and added it etc. I pointed it to the index.vnc file but it will not run, all it says is "Could no launch Menu item Details: Faild to execute child process "/home/administrator/vnc-e4_2_6-x86_linux/JAVA/index.vnc" (permission Denied)" If I alter the permissions of the index.vnc file it stops working completely and the same is true if I run it with the terminal. 

I did also try and install VNC properly as per their site using Alien. It sort of worked however when I run the viewer I get:

"administrator@TOWER-5-LINUX:~$ vncviewer

VNC Viewer Enterprise Edition E4.2.6 for X - built Jul 27 2006 10:18:59
Copyright (C) 2002-2006 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.


Sat Sep  2 00:46:27 2006
 TcpSocket:   connected to 192.168.200.3::5900
 CConn:       Connected to host 192.168.200.3 port 5900
 CConn:       Encryption set to 'Server'
 CConnection: Server supports RFB protocol version 4.0
 CConnection: Using RFB protocol version 4.0
Aborted"

I dunno :confused: .... I have seen other people having the same problem as me but no one seems to have fixed it. Its just annoying as as far as I can see none of the versions that synaptics have will work with the enterprise edition. As I say m8 any help would be really apprciated as I just want to be able to access our windows boxes in a simple way ](*,)

---

### Post by fog_proxy on 2006-09-06
well, I met the same issue too, if anyone have a solution, please help.

---

