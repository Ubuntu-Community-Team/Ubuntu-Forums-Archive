---
title: "Pidgin Crashing With History Error"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by SavageTendencies on 2008-02-12
Hey all.
Sort of new to Linux..

But anywho.
I have been using pidgin and everything was fine.
Until somewhat recently.

Everytime I start pidgin it shows a box telling me

"History Plugin Requires Logging

Logging can be enabled from Tools -> Preferences -> Logging.

Enable logs for instant messages and/or chats will activate history for the same conversation type(s),"

And when I close that window, another comes up telling me 
""" is not responding." 
and asks me to wait for force quit.

I never even get to see my buddy list window.

Help would be GREATLY appreciated.

-ST

---

### Post by nikoPSK on 2008-02-12
> **SavageTendencies said:**
> Hey all.
Sort of new to Linux..

But anywho.
I have been using pidgin and everything was fine.
Until somewhat recently.

Everytime I start pidgin it shows a box telling me

"History Plugin Requires Logging

Logging can be enabled from Tools -> Preferences -> Logging.

Enable logs for instant messages and/or chats will activate history for the same conversation type(s),"

And when I close that window, another comes up telling me 
""" is not responding." 
and asks me to wait for force quit.

I never even get to see my buddy list window.

Help would be GREATLY appreciated.

-ST

maybe run pidgin from terminal like this:

```
pidgin
```

and give output when it crashes?

---

### Post by SavageTendencies on 2008-02-12
I ran it in debug mode in the terminal because it wasn't showing anything normally. 

It ended up repeating this over and over until I force quit.

```

(20:25:02) msim: msim_process_reply: not caching body, no UserName
(20:25:02) msim: msim_process_reply: no callback for rid 3
(20:25:02) msim: msim_parse: got <\persistr\\cmd\257\dsn\0\uid\88352974\lid\1\rid\3\mtf\6\body\Visibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=22885012Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=http:/1/1a378.ac-images.myspacecdn.com/102050/177/130/12050600377_s.pngShowAvatar=TrueLastLogin=128398860600000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=22994496Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=23475809Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=23627917Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=23709763Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24024778Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24138033Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24234173Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24420029Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24753081Headline=On MySpaceIMPosition=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128068252800000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24945463Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=25231778Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=26316202Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=26603238Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=27035268Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=27487916Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128061282600000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28418120Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128176267200000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28514566Headline=Being people that do daytime thingsPosition=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128274328200000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28787557Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=http:/1/1a772.ac-images.myspacecdn.com/102039/117/170/12039740771_s.pngShowAvatar=TrueLastLogin=128316106200000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28873882Headline=Maybe tomorrow, I'll let you borrow some of my insanityPosition=0GroupName=IM FriendsVisibility=1AvatarUrl=http:/1/1b7.ac-imageSelect=0OfflineMsg=SkyStatus=0ContactID=21591889Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=22198021Headline=Position=0GroupName=IM Friends>


```

Not sure if that copied correctly or not. Hope that helps. x.x

---

### Post by nikoPSK on 2008-02-12
> **SavageTendencies said:**
> I ran it in debug mode in the terminal because it wasn't showing anything normally. 

It ended up repeating this over and over until I force quit.

```

(20:25:02) msim: msim_process_reply: not caching body, no UserName
(20:25:02) msim: msim_process_reply: no callback for rid 3
(20:25:02) msim: msim_parse: got <\persistr\\cmd\257\dsn\0\uid\88352974\lid\1\rid\3\mtf\6\body\Visibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=22885012Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=http:/1/1a378.ac-images.myspacecdn.com/102050/177/130/12050600377_s.pngShowAvatar=TrueLastLogin=128398860600000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=22994496Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=23475809Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=23627917Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=23709763Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24024778Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24138033Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24234173Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24420029Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24753081Headline=On MySpaceIMPosition=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128068252800000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=24945463Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=25231778Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=26316202Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=26603238Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=27035268Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=27487916Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128061282600000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28418120Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128176267200000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28514566Headline=Being people that do daytime thingsPosition=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=FalseLastLogin=128274328200000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28787557Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=http:/1/1a772.ac-images.myspacecdn.com/102039/117/170/12039740771_s.pngShowAvatar=TrueLastLogin=128316106200000000IMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=28873882Headline=Maybe tomorrow, I'll let you borrow some of my insanityPosition=0GroupName=IM FriendsVisibility=1AvatarUrl=http:/1/1b7.ac-imageSelect=0OfflineMsg=SkyStatus=0ContactID=21591889Headline=Position=0GroupName=IM FriendsVisibility=1AvatarUrl=ShowAvatar=TrueIMName=NickName=NameSelect=0OfflineMsg=SkyStatus=0ContactID=22198021Headline=Position=0GroupName=IM Friends>


```Not sure if that copied correctly or not. Hope that helps. x.x

hrm, maybe this:

```
sudo apt-get remove --purge pidgin -y && sudo apt-get install pidgin -y
```

---

### Post by SavageTendencies on 2008-02-12
> **nikoPSK said:**
> hrm, maybe this:

```
sudo apt-get remove --purge pidgin -y && sudo apt-get install pidgin -y
```

Nope. I did that and got the same exact thing. 

x.x

---

### Post by nikoPSK on 2008-02-12
> **SavageTendencies said:**
> Nope. I did that and got the same exact thing. 

x.x

:cry:

---

### Post by Gromadusi on 2008-04-15
got the same error, and all i had to do is throwing away the config files

accounts.xml
blist,xml
prefs.xml
status.xml
xmpp-caps.xml

(maybe just the right one would have been enough ;)...it didn't work tough with only throwing away prefs.xml)
this forced pidgin to restart from scratch, and after it started, i put the backupped 'accounts.xml' back in place

---

