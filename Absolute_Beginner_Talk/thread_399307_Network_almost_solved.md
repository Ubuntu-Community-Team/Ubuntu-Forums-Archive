---
title: "Network almost solved"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-04-02
My network problems are almost solved.

I can now access all of my files on the computer that my wife has now taken from me.
I can also share her printer.........only took two weeks, not bad hey.

I'm left with one slight niggle.
My works laptop. It can SEE my Ubuntu computer, but it won't move into the file area.
I've set up sharing in my home folder thusly

Share Folder> Share with SMB


I ticked ALLOW BROWSING FOLDER
I set DO NOT USE A WINS SERVER

So, where am I going wrong?
Phil

---

### Post by mikeyphi on 2007-04-02
Sorry if I missed it previously - Which OS are you using on your works Laptop?

---

### Post by miggols99 on 2007-04-02
I have the same problem. Try typing the address in the location bar. That works for me.

---

### Post by groeswenphil on 2007-04-02
Sorry.

Microshaft X.P.

---

### Post by mikeyphi on 2007-04-02
Assuming your XP is under ntfs not fat32 you will need this little program (Ext2 IFS for windows) to let your XP side see your ubuntu files - [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by WakkiTabakki on 2007-04-02
I've experienced similar problems (although, I'm not 100% it was the exact same prob).
Try this on the Ubuntu machine:
```
sudo gedit /etc/nsswitch.conf
```
and add wins to the 'hosts:' line. Mine reades
```
hosts: files mdns4_minimal [NOTFOUND=return] dns _wins_ mdns4
```
<edit2>You probably need to restart the Ubuntu machine (a 'sudo /etc/init.d/networking restart' may be enough, though)</edit2>

<edit>Just read mikeyphi's post... Just want to make sure we're takling about the same thing here... it's about network shares, right? The IFS is only for when you've got a linux partition (specifically formatted with ext2/3) on the same machine as a windows partition and want to be able to access the linux-files  when booted into windows.
From what I understand, your problem is that you can't see the Ubuntu share over the network from a different computer running windows, right? In that case, the wins-thing *may *be a solution</edit>

/N

---

### Post by groeswenphil on 2007-04-02
You're right.
Ext2 IFS for windows is for a duel boot machine and you're trying to see your Linux partition from the Windows side..........neat though, I can use that.

Trying the other option, but I'm going to re-boot first.
Thanks,
Phil

---

### Post by groeswenphil on 2007-04-02
Just tried this.

hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4

And ever since, I haven't been able  to get on line with Ubuntu.....although I can in Windows.

I tried setting it back to 
hosts: dns mdns

but no luck at the moment.

Any suggestions?
Phil

---

### Post by groeswenphil on 2007-04-03
[SIZE="7"]'tis O.K.
Back on line now.
:lolflag: [/SIZE]

---

### Post by WakkiTabakki on 2007-04-03
Hehe, welcome back!
Hmmm... Just went through some posts old posts, and I think the wins-thing was to solve a problem where the Ubuntu comp couldn't connect to other computers by name (only by IP)...

Your problem may be caused by not having the proper permissons.
Did you add an smb-user to the Ubuntu machine matching the windows user?
```
> sudo smbpasswd -a <UserNameOnTheWinMachine>
New SMB password: <PasswordOfTheWinCompUser>
Retype new SMB password: 
```

And then enable it
```
> sudo smbpasswd -e <UserNameOnTheWinMachine>
```


/N

---

### Post by groeswenphil on 2007-04-03
I'll give it a go right now................trembling with anticipation.

:-({|= 
Phil

---

