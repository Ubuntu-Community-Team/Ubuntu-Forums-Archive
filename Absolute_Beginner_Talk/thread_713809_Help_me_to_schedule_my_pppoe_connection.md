---
title: "Help me to schedule my pppoe connection"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by praveenpious on 2008-03-03
Please help me to schedule my pppoe connection using gnome-schedule or crontab. I dial out by issuing **sudo pon dsl-provider** on the terminal window. How do i schedule to automatically dial the connection at a specified time, say 2:05am !!

---

### Post by es@urito on 2008-03-03
```
sudo crontab -e
```

To edit the root crontab. Configuring a cron job is dead simple, look at this guide [http://www.linuxhelp.net/guides/cron](http://www.linuxhelp.net/guides/cron)

---

### Post by net-reg on 2008-03-08
hi,
   u must b from india and having bsnl connection if u want to dial out at 2am and shutdown at 6am:)

  do this --
              #gksudo gedit /etc/sudoers        (this will open the 'sudoers' file. in it add - 
                                                                         Defaults:username	timestamp_timeout=600
                                                                   at username give ur username
                                                               this makes sudo not ask for password for 600min)

           #at 2am tomorrow  (press enter)              (read manpage for 'at' --  #man at  )
              >pon dsl-provider
              >(press ctrl-D)

          #at 6am tomorrow (press enter)
            >poff
            >sudo shutdown -h now
            >(ctrl-D)

          now what do u want to do at that unearthly hour? dwnld torrent ofcourse :)
           remember to give sudo command in the 'terminal' in which u give at command
          can give anyhting like #sudo firestarter
           (so that now onwards 600 min counting will start)

        b a geek use rtorrent  :)

---

