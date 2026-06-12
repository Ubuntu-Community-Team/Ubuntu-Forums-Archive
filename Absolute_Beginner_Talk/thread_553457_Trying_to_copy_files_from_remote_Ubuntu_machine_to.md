---
title: "Trying to copy files from remote Ubuntu machine to local machine"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-09-17
Okay so I have two computers with Ubuntu; one desktop (with 7.04) and a laptop (with 6.06). I want to connect to the 6.06 laptop with ssh so I followed the instructions on ubuntuguide.org and installed OpenSsh.

I'm able to connect to the machine through ssh, and I can type commands and such.

But when i want to copy a folder to my local machine using this command (found at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server):](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server):)

```
scp -r username@192.168.0.2:/home/username/remotefile.txt
```

or (this is the real command I'm using, the example one is above, since the machine is on a local network, I think I'm safe even though I'm showing the IP address of my local machine):

```
scp -r jeffrey@192.168.0.106:/home/jeffrey/Desktop/lulzz
```

it doesn't work. I get this result:
```
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2

```

So obviously I have the wrong syntax. I think the problem stems from the fact that the directions are for a particular file, and I need to copy a folder.

Help! Thanks.

---

### Post by bodhi.zazen on 2007-09-17
Just like cp you must specify a location to copy to :

```
scp -r jeffrey@192.168.0.106:/home/jeffrey/Desktop/lulzz **[color=blue]~**[/color]
```

Will copy to your home directory.

You must have permissions to access both what you want to copy and where you want to copy to.

---

### Post by asmoore82 on 2007-09-17
you need to tell it where to go; so if you want it to copy remote files to your **current working directory**
add a single dot '.' at the end of the command ...

```
~$ scp -r user@remote:/path/to/file .
```

also, in Gnome, you can interact with remote filesystems via ssh graphically quite nicely ...

open "Places -> Connect to Server..."
then change the "Service type" to "SSH" (It should be the first one in the list)
then fill out other info as necessary (IP, username, default folder)
then you get a remote folder mounted on your desktop just as
smooth and easy as Windows/Samba filesharing but 100% secure.

---

### Post by louieb on 2007-09-17
don't know much about scp but you can use the file browser. open places > connect to server > chose ssh as the service type and enter the ip in the box labeled server. if you want you can give it a name. click connect and your done. Now your ssh connection is just another place on the places menu.

---

### Post by akiratheoni on 2007-09-17
Thanks for the replies. I think it's copying now.

The reason why I asked for scp is because I DID connect using Nautilus, but whenever I would copy the files over, it would 'time out' and the larger files wouldn't copy over. It's copying over, though. Thanks! I read about the '.' but I didn't know what it meant, so I didn't add it. But I think that's what was wrong.

---

