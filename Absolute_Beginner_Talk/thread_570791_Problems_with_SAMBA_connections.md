---
title: "Problems with SAMBA connections"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2007-10-08
Ok, I beg you dont flame me! - I know I have posted problems on this before.

I just felt that I might get a better response if I post a more detailed description. 

Here goes!


I am trying to share files between my Ubuntu Linux  and Mac OS X.

Ubuntu is running on VMWARE - (Virtual Machine).

I have installed Samba -

Created  a samba password using:
```

sudo smbpasswd -a <username> 
```

The username I used was Shane. So I typed:

```
sudo smbpasswd -a shane
```

I then added this user to the smbusers file:

```
sudo vi /etc/samba/smbusers
```

This is the format I entered it in:

```
administrator = "shane"
```

I assume the above maps the ubuntu user "administrator" to the samba user Shane?

For testing purposes I am using the password "support"

I have configured the shared home directories as expected.

On the mac:

Finder -> GO -> Connect to server
I enter the details in the image below.

[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Picture1-3.png[/IMG]

Then there is a pause when connecting like so:

[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Picture2-3.png[/IMG]

I am then presented with this window: 

[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Picture3.png[/IMG]

I change the fields (using the password "support") like so:

[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Picture4.png[/IMG]

I click connect and this is what I get :

[IMG]http://i100.photobucket.com/albums/m14/shanekillian/Picture5.png[/IMG]






If anyone has any suggestions  I would appreciate hearing them.
If anyone has spotted that I have done something wrong it would be a great help to point it out.


I think I should add that I am using Ubuntu Server with no GUI (Command Line Only).

---

### Post by myk.dinis on 2007-10-09
ok...you need to add a line in smbusers that says 
shane = shane

that's if you have an account on your ubuntu machine with that name...

i.e. if you login to ubuntu with the usenme shane just set it like I wrote...

Make sure you have these flags set up in smb.conf

socket options = TCP_NODELAY 
map to guest = Bad User
restrict anonymous = yes
guest ok = no
domain master = no
preferred master = no

and make sure this is also there...

[share_name]
path = /path/to/share
available = yes
browsable = yes
public = no
writable = yes

and in your smbusers

# Unix_name = SMB_Name1 SMB_Name2 ...
root = administrator
nobody = guest smbguest pcguest
shane = shane

That way when you browse the smb machine via windows the share will show up but you won't have access unless you either have the root password...which you shouldn't use (too dangerous) or you are shane

Any user you want to have access to the share you need to specify it in the smbusers file...

that way you won't have any anonymous access to your files...

and make sure the correct workgroup is called in the smb.conf like this:

max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto
workgroup = <Your Workgroup>  <--- be sure to remove the angle brackets...

Key points to remember...no quotes around names and be sure to use proper casing...

best of luck...hope this helps...

BTW, you can ping the virtual machine using your mac right?

If not then everything I just wrote is moot till you fix that...It looks like it's working properly (the networking part) but you can never be 100% till you test it.

Cheers,
Myk

---

