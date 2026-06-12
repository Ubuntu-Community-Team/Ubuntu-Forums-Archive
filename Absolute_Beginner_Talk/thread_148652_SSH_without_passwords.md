---
title: "SSH without passwords"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-03-22
Hello everyone

If I have a cron job that executes on a remote machine after logging in through ssh, how do I do it? I mean,the cron job can not ask for a password.. 

I know there is a way to do it, but I don't know how to search for it. All my searches have only revealed using passphrases instead of passwords (using dsa/rsa keys) but still that can't be done in a cron job.

Thanks !

---

### Post by nanotube on 2006-03-22
from the ssh man page:

ssh implements the RSA authentication protocol automatically.  The user creates his/her RSA key pair by running ssh-keygen(1).  This stores the pri&#8208;
     vate key in $HOME/.ssh/identity and stores the public key in $HOME/.ssh/identity.pub in the user’s home directory.  The user should then copy the
     identity.pub to $HOME/.ssh/authorized_keys in his/her home directory on the remote machine (the authorized_keys file corresponds to the conventional
     $HOME/.rhosts file, and has one key per line, though the lines can be very long).  After this, the user can log in without giving the password.

also from the ssh manpage is the option "-i", to specify the identity file to use (if the cron job does not pick it up correctly)

so, do the key thing, then when running the cron job, specify the identity file with -i in your commandline, and it should be able to log in without using a password. (feel free to read the rest of "man ssh" for more detail).

another thing is that the server you are logging into has to have rsa identification enabled. ("man sshd" for more details). 

have fun! :)

out of curiosity, what is the cron job supposed to do?

---

### Post by harisund on 2006-03-22
Actually, we have a super computer at school that's running a long simulation (takes a couple of days.) Periodically, we log in, check if the simulation is still running, and get the output (using scp actually) file. 

Then the script compares the output file with the old output file to see whether any new output has resulted from the simulation. 

Whenever there is a change, we are then sent an email that there has been a new result.. 

Thanks a lot anyway ! I simply *love* these forums..

---

### Post by nanotube on 2006-03-23
hehe, sounds cool! :)

and by the way, there IS a way for a cron job to supply a password to the remote system. there is a package called "expect" that can interact with interactive programs using a script, so you could potentially even log in through ssh by using expect and having it supply a password.

of course, you should only resort to that if the key method does not work for you for some reason. :)

---

