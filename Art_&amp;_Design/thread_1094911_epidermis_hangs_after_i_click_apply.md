---
title: "epidermis hangs after i click apply"
date: 2009-03-13
forum: Art &amp; Design
---

### Post by nikonfrz on 2009-03-13
i just installed the latest version of epidermis and when i click apply it just hangs with "you may need to enter password to gain root access" and does nothing :\ can someone help me troubleshoot?

---

### Post by Orlsend on 2009-03-13
Can you run it in the terminal? And tell us where it gets stuck and whats the outcome.

---

### Post by nikonfrz on 2009-03-13
i went in terminal and did "epidermis" and it said

```
root@vpkeebs-laptop:/home/vpkeebs# epidermis
Epidermis, Copyright (C) 2008 David D Lowe
Epidermis comes with ABSOLUTELY NO WARRANTY; for details click on the About button, License
This is free software, and you are welcome to redistribute it
under certain conditions; for details click on the About button, License
```

then i got a bug window with this message when it tried to load

```
Traceback (most recent call last):
  File "/usr/bin/epidermis", line 15, <module>()
            import epidermis.epidermis
            epidermis.epidermis.main()
  variables: {'epidermis.epidermis.main': ('local', <function main at 0x90c6374>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 1430, main()
        """launches start(sys.argv)"""
        start(sys.argv)
  variables: {'start': ('global', <function start at 0x90c06bc>), 'sys.argv': ('global', ['/usr/bin/epidermis'])}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 1403, start(args=['/usr/bin/epidermis'])
               print debuginfo.debuginfo()  
            app = EpidermisApp()
            gtk.main()
  variables: {'app': (None, None), 'EpidermisApp': ('global', <class epidermis.epidermis.EpidermisApp at 0x90c135c>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 246, __init__(self=<epidermis.epidermis.EpidermisApp instance at 0x90c592c>)
            if not os.path.exists(MY_DATA_HOME):
                client.set_bool("/apps/epidermis/apply_system_wide",False)
                client.set_string("/apps/epidermis/repo_url", "http://download.tuxfamily.org/epidermis/ghns/downloads.xml")
  variables: {'False': ('builtin', None), 'client.set_bool': ('local', <built-in method set_bool of gconf.Client object at 0x90d0784>)}
GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

debuginfo.debuginfo error
```

it will load from the menu but not terminal :\

---

### Post by Flimm on 2009-03-13
Hi, I'm the developer of Epidermis. Could you also include which version of Ubuntu you're running,the version of Epidermis, and the output of this command: python --version

---

### Post by nikonfrz on 2009-03-13
ubunutu 8.10
epidermis 0.2.2
output of "python --version"

```
vpkeebs@vpkeebs-laptop:~$ python --version
Python 2.5.2
vpkeebs@vpkeebs-laptop:~$ 

```

---

### Post by Orlsend on 2009-03-14
Just to be safe. Epidermis only works on gnome, I just said that because in your profile it says you use Kubuntu. Ill try to get Flimm over and see what he thinks of your error output.

---

### Post by nikonfrz on 2009-03-14
i use ubuntu. sorry i didn't notice it said kubuntu :\

---

### Post by nikonfrz on 2009-03-15
bump?

---

### Post by Orlsend on 2009-03-15
Sorry i tried to contact Flimm, but I was informed he was in a Holiday though he should be back by tomorrow. I am going ahead and post this this in Launchpad.

---

### Post by Flimm on 2009-03-19
For some reason, the gconf module is refusing to cooperate. Try running the script I've attached and post the output please.
Oh, BTW, I'd appreciate it if users only post their own bugs, Orlsend, for reasons I've explained [on the bug tracker](https://bugs.launchpad.net/epidermis/+bug/343315).

---

### Post by nikonfrz on 2009-03-20
am i to make this an executable? if so i did, and it opened epidermis and i still get the hang after i click apply :\ if i'm not to run as executable please specify as im new to ubuntu and not sure what you want me to do

---

### Post by Flimm on 2009-03-20
Sorry, here are more specific instructions:
[list][*]download the script and put in your home directory
[*]open a terminal
[*]make it executable by running:
```
chmod +x gconf_test.py
```
[*]run the script and post the output:
```
./gconf_test.py
```[/list]

---

### Post by nikonfrz on 2009-03-20
"a programing error has been detected during the execution of this program"
```
Traceback (most recent call last):
  File "./gconf_test.py", line 22, <module>()
    import epidermis.epidermis
    epidermis.epidermis.main()  variables: {'epidermis.epidermis.main': ('local', <function main at 0x900648c>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 1430, main()
        """launches start(sys.argv)"""
        start(sys.argv)
  variables: {'start': ('global', <function start at 0x90057d4>), 'sys.argv': ('global', ['./gconf_test.py'])}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 1403, start(args=['./gconf_test.py'])
               print debuginfo.debuginfo()  
            app = EpidermisApp()
            gtk.main()
  variables: {'app': (None, None), 'EpidermisApp': ('global', <class epidermis.epidermis.EpidermisApp at 0x90012fc>)}
  File "/usr/lib/python2.5/site-packages/epidermis/epidermis.py", line 246, __init__(self=<epidermis.epidermis.EpidermisApp instance at 0x9004d2c>)
            if not os.path.exists(MY_DATA_HOME):
                client.set_bool("/apps/epidermis/apply_system_wide",False)
                client.set_string("/apps/epidermis/repo_url", "http://download.tuxfamily.org/epidermis/ghns/downloads.xml")
  variables: {'False': ('builtin', None), 'client.set_bool': ('local', <built-in method set_bool of gconf.Client object at 0xb7a5116c>)}
GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

debuginfo.debuginfo error
```




and terminal said this:
```
root@vpkeebs-laptop:/home/vpkeebs# chmod +x gconf_test.py
root@vpkeebs-laptop:/home/vpkeebs# ./gconf_test.py
gconf.__file__ : /var/lib/python-support/python2.5/gtk-2.0/gconf.so
Traceback (most recent call last):
  File "./gconf_test.py", line 12, in <module>
    print "/apps/nautilus/preferences/show_desktop :", client.get_bool("/apps/nautilus/preferences/show_desktop")
GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
/apps/nautilus/preferences/show_desktop : Epidermis, Copyright (C) 2008 David D Lowe
Epidermis comes with ABSOLUTELY NO WARRANTY; for details click on the About button, License
This is free software, and you are welcome to redistribute it
under certain conditions; for details click on the About button, License
root@vpkeebs-laptop:/home/vpkeebs# 

```

---

### Post by Flimm on 2009-03-21
> GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
The error is pretty strange, and is not a bug in Epidermis. It seems like your Gconf system is broken. Do you get any error messages when you log in? What happens when you put this command in the shell:
```
gconftool-2 --get /apps/nautilus/preferences/show_desktop
```

---

### Post by nikonfrz on 2009-03-22
```
vpkeebs@vpkeebs-laptop:~$ su
Password: 
root@vpkeebs-laptop:/home/vpkeebs# gconftool-2 --get /apps/nautilus/preferences/show_desktop
Failed to get value for `/apps/nautilus/preferences/show_desktop': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
root@vpkeebs-laptop:/home/vpkeebs# 
```

this sucks :(

---

### Post by Flimm on 2009-03-23
I feel for you :icon_frown: and I don't know how to fix the problem. Why don't you go to [Beginner Talk](http://ubuntuforums.org/forumdisplay.php?f=326) and show them the error you get when you use gconftool-2?

---

### Post by nikonfrz on 2009-03-23
alright. well thank you so much for trying to help me figure this out. i appreciate it very much :)

---

