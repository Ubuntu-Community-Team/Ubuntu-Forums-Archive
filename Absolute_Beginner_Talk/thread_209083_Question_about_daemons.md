---
title: "Question about daemons"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by ctrl4ltdeleteme on 2006-07-04
I don't have too much experience with linux.  I've just installed dapper drake 
the server version and I used apt-get to install vsftpd.  The setup seemed to 
work fine.  When I was done I could access the ftp from my network.  Then I 
changed some options and, so they would take effect, killed the program with
sudo kill [process number].  

I followed this tutorial for pretty much everything I did:
[https://help.ubuntu.com/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/ubuntu/serverguide/C/ftp-server.html)

Then, I tried to restart it using:
sudo /etc/init.d/vsftpd start

the console replied with:
* Starting FTP server: vsftpd 

I checked to see if it was running with ps -A, and it's not.
I also tried using
sudo /etc/init.d/vsftpd start &

to this the console says that it's starting the server, but then i get this:
[1]+  Done                    sudo /etc/init.d/vsftpd start

the only thing I could think of is that I screwed something up when I killed the daemon manually.  Also any insight as to how to keep the daemon running would be appreciated.  Thanks in advance.

---

### Post by opus on 2006-07-04
To control the daemons that are running on your server use the /etc/init.d scripts for both starting and stopping.  Another useful command is "restart".  So /etc/init.d/vsftpd restart would restart the vsftpd daemon.

The scripts are setup to launch the daemon process and then exit.  The daemon process is launched in the background.  The script does not continue executing which is why you are getting the done message after using the "&" after the command.

vsftpd may be setup to run as an inetd service so it would only be running if someone were accessing it, and it would get shut down when it is idle.

Aaron

---

### Post by steve.horsley on 2006-07-04
Have a look at the startup script and see if it outputs to a log file. Also have a look at the changes you made to the configuration file. You seem to be trying to start it correctly, so I guess that the modified configuration is upsetting it.

---

