---
title: "Help joing an Ubuntu chat room from pidgin"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by High_Yield on 2007-12-19
Hi-

I have Gutsy up and running well but have a MAJOR issue with samba on my NAS.
Pidgin is running fine but I've never joined a "support chat" and cannot coonect to "#ubuntu".  It's a total noob question but any advice would help.

Pidgin asks for a room, server, handle, and password when I click "join chat".

Thanks again in advance - B

---

### Post by bump_ on 2007-12-19
I am not sure if Pidgen can be used as an IRC client, but perhaps someone else will come along to prove me wrong.

The way I chat is with chatzilla, an add-on for firefox. Just download it here [https://addons.mozilla.org/en-US/firefox/addon/16](https://addons.mozilla.org/en-US/firefox/addon/16), and it will install itself. Restart firefox, go to tools>chatzilla. Then you can just click on "freenode" and type /join #ubuntu.

Hope it helps

---

### Post by NateMan on 2007-12-19
xchat is nice gnome irc client. I've used it in the past to go to #ubuntu and it seems to work great.

---

### Post by p_quarles on 2007-12-19
Yes, Pidgin can be used as an IRC client, and there's really no need to clutter the system with a separate dedicated client. 

Anyway, here's the info you need:
server: irc.freenode.net
room: #ubuntu
handle: whatever you want, as long as it's not taken by a user already in the room
password: not necessary

---

### Post by bump_ on 2007-12-19
Yes p_quarles is correct. i was playing around on pidgen and it turns out you have to make a new account with IRC as the protocol.

---

### Post by High_Yield on 2007-12-19
Thanks guys - almost there....

I have created and IRC account and it is selectable from the dropdown list while trying to join chat - but - I cannot connect to #ubuntu.  I get no error messages - nothing - just sits there,

The following options disappear when selecting an IRC type account:
- Server
- Handle
- Password
And a new one appears called "Exchange" which simply accepts a numeric value,

In the IRC account Advanced setup is what appears to be the "Server" option - so I entered irc.freenode.net.
I've tried changing the port to 443 but - no go either way - ugh:roll:

Will keep trying in the meantime and post results - B

---

### Post by High_Yield on 2007-12-19
Well,

in my last post I stated "IRC" but was actually fumbling with the "ICQ" settings - whoops:confused:

So now - I've created a real IRC account and the "connecting..." text is gone and I appear to be "in".

I then created a new Conversation using Ctrl+M and put in #ubuntu and a nice new conversation tab opens up.  From here I do not know.  I've said "hello" etc.. but either nobody is in the room, saying hello back to me, or I'm still doing something wrong,

Again - any assistance is appreciated as I am an IRC noob.\\:D/

---

### Post by p_quarles on 2007-12-19
Try entering the following:
```
/join #ubuntu
```
There are usually about 11,000 people logged in at any given moment (don't worry, most of them aren't sending messages), so if it's empty, you're definitely in the wrong place.

---

### Post by High_Yield on 2007-12-19
OK - got it finally....

Again my bad but "new message" is different than "new chat".

I've also checked off SSL and using port 443 as this article suggests.
[http://www.freesoftwaremagazine.com/articles/pidgin?page=0%2C2]("http://www.freesoftwaremagazine.com/articles/pidgin?page=0%2C2")

Thanks for pointing me in the right direction and I hth someone...

Regards - B

---

