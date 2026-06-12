---
title: "Running Python Script in Session Manager"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by warnetgm on 2005-09-08
I want my python script run everytime login.
In WinXP I've done this simply by placing shortcut of my program into StartUp Folder
In Ubuntu I tried using session manager in Startup tab adding :
```

python /home/user/program.py

```

Well it being loaded after I tested to logoff and login, but unfortunately the status is "TRASH" icon which I've read in manual mean not started in current session.

So how to make my python script executed every login using session manager ?

Thank You

---

### Post by warnetgm on 2005-09-11
Halo ?
Please, anyone experts in Running Python Script on Session Manager, Help me :)
Please

---

### Post by warnetgm on 2005-09-14
Please Help Experts :)

---

### Post by Nequeo on 2005-09-14
I'm not an expert... But you could try adding

#!/usr/bin/python to the first line of your python script (it absolutely MUST be the very first line), mark the program as excutable
```

chmod +x propgram.py

```
and they just call it by its name. I.e. make the command 'program.py' in the session manager.

Apart from that, do you have any way to verify that the program has run/is running? I don't know much about the Gnome session manager, but are you sure the trash icon couldn't also mean that the Python program doesn't have an associated icon, or something similar?

---

### Post by warnetgm on 2005-09-15
Very Thanks for your care of a newbie :)

Anyway this is my code :

```

#!/usr/bin/python2.4

from socket import *

def main():
        s = socket(AF_INET, SOCK_DGRAM)
        hostname = '192.168.100.100'
        port = 1973
        s.connect((hostname, port))

        code = chr(203);
        stationid = '30';
        s.send(code + code + stationid + ' Games')

        code = chr(203) + chr(214) + chr(201) + chr(198) + chr(001)
        s.send(code + 'LINUX CLIENT PROGRAM' + stationid);

if __name__ == "__main__":
        main()

```

I've tried to use :
```

chmod a+x /home/user/client.py

```

And called it in session manager :
```

/home/user/client.py

```

but still it doesn't being executed, it has trash icon status which mean being pending or somekind, while actually if I run the program in Terminal :
#python
>>import client.py
>>client.main()

it is ok being executed well.

What is the problem please ?

Thank You :)

---

### Post by warnetgm on 2005-09-20
Is there any expert, know about session manager ?

Thank You :)

---

### Post by David Marrs on 2005-10-09
I think you add the file (or a symbolic link to the file) to /etc/rc3.d/, but don't take my word for it. I am not an expert!

---

### Post by woodenlink on 2006-06-21
[QUOTE=warnetgm]Very Thanks for your care of a newbie :)

:
:

What is the problem please ?

Thank You :)[/QUOTE]

There are several ways to let Ubuntu execute your script, either way, you have to make sure that the script is readable by the user who will execute it. To be safe;
1. Make a copy of it at /usr/bin
```

cp /home/user/client.py /usr/bin/

```
2. grant execution to everyone
```

chmod a+rx /usr/bin/client.py

```

Next, if you want each user to execute the code automatically on every login:
a. Add the path to /etc/profile (please backup the file before you execute this code)
```

echo '/usr/bin/client.py' >> /etc/profile

```
It works just like StartUp Folder at WinXP

b. If you need only certain user executing the code, add the path to /home/username/.bash_profile
e.g if the code apply only to yourself, do this:
```

echo '/usr/bin/client.py' >> /home/warnetgm/.bash_profile

```
The script will be executed every time you login, just you. Other users won't be affected.

Next, if you don't need the code executed every login, just the first time you start your server. Choose one:
a. Add the path to /etc/init.d/rc
```

echo '/usr/bin/client.py' >> /etc/init.d/rc

```
b. Make a symbolic link in /etc/rc2.d or /etc/rc3.d or /etc/rcS.d
```

ln -s /usr/bin/client.py /etc/rcS.d/S99clientscript

```
The S indicating the script is executed when entering the runlevel.
The #99 is the priority, means the script executed after lower number script have been executed.
The last field is the name you give.

Good luck with your script!
ps: you need root account to execute the given code
```

sudo su -
password: *******

```

---

### Post by oskarloko on 2006-08-30
Well, other way
> 
sudo echo '/usr/bin/client.py &' >> /etc/rc.profile

as far as I know, rc.profile is a file that is executed everytime  ubuntu is booted, at last time... you can edit and launch command with it.

(Really it's placed at S99rc.profile on /etc/rcS.d - i think )

---

