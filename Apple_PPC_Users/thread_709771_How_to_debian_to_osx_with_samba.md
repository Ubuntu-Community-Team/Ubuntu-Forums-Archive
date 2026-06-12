---
title: "How to debian to osx with samba"
date: 2008-02-27
forum: Apple PPC Users
---

### Post by oswaldkelso on 2008-02-27
I just set up samba on my main debian box to access my osx machine and any other boxes I acquire. I run blackbox and rox-filer so if anyone know of an easier (less heavy way) please post. I will say its slow but  it does work.. so I assume ubuntu will also. Now just to figure out osx to debian :)

 first on debian/ubuntu install samba :)

in osx (10.4)

goto system preferences/network /configure /tcpip and configure IPv4. set to dhcp with manual address and give your self a static ip. e.g.192.168.0.203 or 192.168.1.203 depending on your router. click &#8220;apply now&#8221; and &#8220;show all&#8221; to go back to system preferences.

go to system preferences/sharing check the &#8220;windows sharing&#8221; box highlight it and read the address at the bottom, this should show your static address. i.e. 192.168.0.203 and user name. note it down.

in debian

open either nautilus or konquorer and open location

##################################################
in nautilus ctl L

smb://osxuser@osxstaticaddress/osxuser

e.g.

smb://joebloggs@192.168.0.203/joebloggs

wait&#8230;&#8230;..

you should be asked for a password&#8230;.. enter joebloggs password

##################################################

in konquorer ctl O (O for Open)

smb://osxuser@osxstaticaddress/osxuser

e.g.

smb://joebloggs@192.168.0.203/joebloggs

wait&#8230;&#8230;..

you should be asked for a password&#8230;.. enter joebloggs password

done.

EDIT: according to synaptic it appears that I **dont** have samba installed  just libsmbclient so it must be using the osx side of things.

---

