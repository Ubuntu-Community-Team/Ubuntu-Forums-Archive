---
title: "How to avoid ANNOYING PASSWORDS for Synaptic, Network, and so on"
date: 2007-05-07
forum: Assistive Technology &amp; Accessibility
---

### Post by asbesto on 2007-05-07
[B]note: FOR THE SOLUTION JUMP TO MY LAST POST HERE. Testing for 9.04 :)
[/B]
Well, 

I log into MY laptop using GDM; to be more precise, I automatically log in after 10 seconds of GDM inactivity, because is my laptop, because it doesn't contain secure data, because mine is the only account in it, and because I don't care to be paranoid with my laptop. 

So, for me is very ANNOYING the password request every time I launch, for example, Synaptic Package Manager, or Network config, or whatsoever the hell I want.

Is there a way to avoid all those password requesters ?!?!??!

p.s.

answers like "THIS IS BAD TO SECURITY" or "HEY 1'M A K00L K-R4D H4CK3RZ y0 dunn0 wh4t th3 h3ll 1s c0mput3rz s3kur1ty go use w1ndow$ 1nst3ad" go directly in /dev/null, garbled with urandom contents and with my blessing of a cruel death.


:lolflag:

---

### Post by ticopelp on 2007-05-07
HEY 1'M A K00L K-R4D H4CK3RZ y0 dunn0 wh4t th3 h3ll 1s c0mput3rz s3kur1ty go use w1ndow$ 1nst3ad!

But seriously, I guess you could always log in as root if you wanted, or make an admin user.

[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)

But I do have to say in good conscience that I don't recommend the whole "logging in as root" thing.

---

### Post by srt4play on 2007-05-07
OH NOES THIS IS BAD TO SECURITY!

If you don't mind entering it once per session, you can do what I do:

Be very careful with this because any typos while editing this can kill your ability to log into the system.

sudo visudo

Add "timestamp_timeout=-1"  to the end of the line that says

Defaults        !lecture,tty_tickets,!fqdn

to make it look like

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=-1

---

### Post by RCC2k7 on 2007-05-07
Actually I do the opposite. On my desktop PC, I have autologin enabled, because it's my computer, I live alone and I don't want the WindowsNT-style bureaucracy of typing a username and password every time I boot MY computer.

Now for my laptop, the story is different. Mobile computers should be password-protected. If someone steals your laptop, you don't want them to have easy access to your files.

But Linux security is a pain for accessibility. In order to get Orca to speak and track on secured applications (such as Synaptic), you need to do some funky hacking, and even then, Orca will work on secure apps, but won't speak or track on non-secure apps until you have closed the secure app.

Something needs to be done.

---

### Post by calraith on 2007-05-07
I just added:
calraith ALL=NOPASSWD: ALL
as the last line of sudoers.  As srt4play mentioned, use the command "visudo" to modify your sudoers file.

---

### Post by asbesto on 2007-05-08
> **calraith said:**
> I just added:
calraith ALL=NOPASSWD: ALL
as the last line of sudoers.  As srt4play mentioned, use the command "visudo" to modify your sudoers file.

and here's the winner. With this I solved the problem. tnx ;)

:guitar:

---

### Post by calraith on 2007-05-08
Victory Is Mine!@!!1

---

### Post by asbesto on 2007-05-11
EHM, 

i talked too fast :(

Synaptic and so on was already asking me for the password :(

So, i found another HORRIBLE solution: I just added

```

asbesto ALL=NOPASSWD: ALL

```

in my /etc/sudoers.

This obviously expose my account to every kind of risk when leaving my shell open, but really: I DON'T CARE. 
:lolflag: 

Now, no more annoying passwords. 

:)

p.s. if someone know an elegant solution instead of this dirty trick, please write it here!

:guitar:

---

### Post by calraith on 2007-05-11
Install [fail2ban]("http://www.fail2ban.org/wiki/index.php/Main_Page") and I think you'll be ok leaving your sudoers file the way it is.  =)

calraith ftw!

---

### Post by asbesto on 2007-09-14
... just reinstalled UBUNTU on my "new" thinkpad T40 ... 

and I have the same problems!

noticed two problems:

1) I had to be added to the "sudo" group in /etc/group

and

2) the correct line in /etc/sudoers seem to be 

asbesto ALL=(ALL) NOPASSWD: ALL

Also, this is my /etc/pam.d/gdm :

[I]root@gemini:/etc/pam.d# cat gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
@include common-pamkeyring
# from [http://ubuntuforums.org/showthread.php?t=316927](http://ubuntuforums.org/showthread.php?t=316927)
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

[/I]

now it's all working, no more annoying passwords. :)

---

### Post by asbesto on 2008-01-05
After a gutsy to feisty upgrade, I lost every config file for this. So here I repost what I suppose is the definitive ultimate guide for not having the balls crushed by passwords anymore. It can work also on 8.10 and 9.04 ...

As **root**:

1. **apt-get install libpam-gnome-keyring**


2. if you don't have it, create a file named 
    
     **/etc/pam.d/common-pamkeyring**

   containing:

[B]
      auth     optional    pam_keyring.so try_first_pass
      session  optional    pam_keyring.so
[/B]

3. edit **/etc/pam.d/gdm** adding this line at the bottom of the file:

**@include common-pamkeyring**

and please COMMENT OUT those lines:

[B]
# auth    optional        pam_gnome_keyring.so
# session optional        pam_gnome_keyring.so auto_start
[/B]

4. Create, if doesn't exist, the "wheel" group, editing /etc/group, and add your user to it 

5. add this in **/etc/sudoers using "visudo"**:

**yourusername ALL = NOPASSWD: ALL **

6. add those things in **/etc/pam.d/sudo** :

[B]
auth sufficient pam_rootok.so
auth required pam_wheel.so
auth sufficient pam_wheel.so trust
[/B]

7. enable this in your **/etc/pam.d/su**

   [B]# Uncomment this if you want wheel members to be able to
   # su without a password.
   auth       sufficient pam_wheel.so trust  
[/B]

8. restart the whole X damn thing

[U]AND LIVE IN HAPPINESS
[/U]

:popcorn::lolflag::guitar:

---

### Post by asbesto on 2009-02-11
Tested on 9.04, it seem OK. Also, if you want to get rid of PolicyKit asking you again for the same password, just edit /etc/PolicyKit/PolicyKit.conf AS HERE BELOW:

> 
<config version="0.1">
    <match user="root|YOUR_USER_HERE">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin|wheel"/>
</config>



---

