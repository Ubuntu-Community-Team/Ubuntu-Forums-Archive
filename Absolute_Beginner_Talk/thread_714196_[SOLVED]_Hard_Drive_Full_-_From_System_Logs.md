---
title: "[SOLVED] Hard Drive Full - From System Logs"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by skozzy on 2008-03-03
I was testing k9copy dvd program last night, I left it running over night and in the morning my HD was full. I scanned the drive and found 3 log files at 6.5gig each, how to I empty these logs. It wont let me move them to the rubbish bin and the log viewer closes after it tries to open them.

The log files are:
var/log/syslog        6.5gig
var/log/kern.log      6.5gig
var/log/messages  6.4gig

I have Ubuntu on a 40gig drive and don't know how to empty these log files.

---

### Post by skozzy on 2008-03-03
By the way, I have the AMD64 version of Ubuntu installed and its only a week old install.

---

### Post by taurus on 2008-03-03
> **skozzy said:**
> I was testing k9copy dvd program last night, I left it running over night and in the morning my HD was full. I scanned the drive and found 3 log files at 6.5gig each, how to I empty these logs. It wont let me move them to the rubbish bin and the log viewer closes after it tries to open them.

The log files are:
var/log/syslog        6.5gig
var/log/kern.log      6.5gig
var/log/messages  6.4gig

I have Ubuntu on a 40gig drive and don't know how to empty these log files.

Applications -> Accessories -> Terminal
```
sudo cat /dev/null > sudo /var/log/syslog
sudo cat /dev/null > sudo /var/log/kern.log
sudo cat /dev/null > sudo /var/log/messages
```
That would set those logs to 0 byte again.

---

### Post by skozzy on 2008-03-04
Thanks for the advice, But when I run those commands it didnt reset the logs to 0 bytes, but appeneded a .0 to each filename.

I rebooted hoping to be able to delete them but it didn't work. The are still showing 6.5gig in size

---

### Post by hyper_ch on 2008-03-04
you could also delete and touch the files... but you might need to chown and chmod them afterwards.

---

### Post by skozzy on 2008-03-04
I just tried the same command but put the .0 after the log names and now im in a worse position, The drive went from 1gig free to 280mb.

---

### Post by skozzy on 2008-03-04
> **hyper_ch said:**
> you could also delete and touch the files... but you might need to chown and chmod them afterwards.

Sorry, but I have no idea what you mean. I'm fairly new to linux.

---

### Post by hyper_ch on 2008-03-04
first do:

```

cd /var/log
ls -al

```

Then write down what permissions and ownerships the files have (probably root.root and 0755)

Once you wrote that down run
```

sudo rm /var/log/syslog && sudo touch /var/log/syslog
sudo rm /var/log/kern.log && sudo touch /var/log/kern.log
sudo rm /var/log/messages && sudo touch /var/log/messages

```

Then you need to set ownership again. That would be root.adm if it was originally owned by it:
```

sudo chown root.adm /var/log/syslog
sudo chown root.adn /var/log/kern.log
sudo chown root.adm /var/log/messages

```

Then you need to set permissions again. That would be root.adm if it was originally owned by it:
```

sudo chmod 0640 /var/log/syslog
sudo chmod 0640 /var/log/kern.log
sudo chmod 0640 /var/log/messages

```

You could combine this all into one shell script

logchange.sh
```

#!/bin/bash

echo "Deleting and reacreate syslog"
rm /var/log/syslog
touch /var/log/syslog
chown root.adm /var/log/syslog
chmod 0640 /var/log/syslog

echo "Deleting and reacreate kern.log"
rm /var/log/kern.log
touch /var/log/kern.log
chown root.adm /var/log/kern.log
chmod 0640 /var/log/kern.log

echo "Deleting and reacreate messages"
rm /var/log/messages
touch /var/log/messages
chown root.adm /var/log/messages
chmod 0640 /var/log/messages

echo ".... finished!"

```

post the above code in logchange.sh, make it executable and then run in on the command line with:
```

sudo sh /path/to/logchange.sh

```

---

### Post by spiderbatdad on 2008-03-04
here's a crude sounding method: ```
gksu nautilus
``` navigate to the files, Edit>>select all>>Edit>>delete.

---

### Post by skozzy on 2008-03-04
[hyper_ch] I had to change some stuff a little as the filenames had changed from an earlier bit of advice and some commands gave errors (see below) but it did work in the end after two attempts.

sudo rm /var/log/syslog.0 && sudo touch /var/log/syslog.0
sudo rm /var/log/kern.log.0 && sudo touch /var/log/kern.log.0
sudo rm /var/log/messages.0 && sudo touch /var/log/messages.0

sudo chown syslog.adm /var/log/syslog.0
sudo chown syslog.adm /var/log/kern.log.0
sudo chown syslog.adm /var/log/messages.0

sudo chmod 0640 /var/log/syslog.0
sudo chmod 0640 /var/log/kern.log.0
sudo chmod 0640 /var/log/messages.0

rm /var/log/syslog.0
touch /var/log/syslog.0
chown root.adm /var/log/syslog.0
chmod 0640 /var/log/syslog.0            <---  Operation not permitted

rm /var/log/kern.log.0
touch /var/log/kern.log.0
chown root.adm /var/log/kern.log.0
chmod 0640 /var/log/kern.log.0          <---  Operation not permitted

rm /var/log/messages.0
touch /var/log/messages.0
chown root.adm /var/log/messages.0
chmod 0640 /var/log/messages.0          <---  Operation not permitted

---

### Post by hyper_ch on 2008-03-04
well, you have to run those commands as sudo (root) otherwise you won't be permitted to do so.

either run each command with sudo as prefix or make a shell script and execute that as sudo ;

I know, the shell is scary, but it improves a lot of things... and can do a lot of things. To get a better idea, consult this site here:  [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by skozzy on 2008-03-04
Big chears on the link to the dos commands. So far its great reading. I book marked it to finish reading later. At least after a few pages I have an understanding (kind of) of the directory structures.

Well you saved me a reinstall. Thanks

---

### Post by hyper_ch on 2008-03-04
You just need to know a few basic commands and put them together in a script... that can save you a lot of time ;)

But still strange that those logs became this big.

---

