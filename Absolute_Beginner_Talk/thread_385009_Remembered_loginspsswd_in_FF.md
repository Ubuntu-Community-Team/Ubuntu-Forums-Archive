---
title: "Remembered logins/psswd in FF"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-03-15
Hi everyone,

Strange thing happened yesterday! I did a Ctrl-Alt-Backspace (to re-log in) and ,to my surprise, this morning all my saved usernames/passwords in FF had disappeared.

Depending on the visited site, I'm afraid I won't remember some of them. 

Why did this happen and any way to get them back? Would they be stored in my box somewhere?

Thanks for your time.

---

### Post by ajgreeny on 2007-03-15
If Firefox was open when you killed X, and you had not previously shut down both firefox and your session normally, then I'm afraid none of the password info would have been saved either to the firefox config or anywhere in your desktop session.  If you had previously shutdown firefox, and just the x session was killed, the passwords should still be in your firefox profile, so make sure you are running the profile you normally do, and hopefully they will all be there.

Why did you do Ctrl+Alt+Backspace instead of ending the current session the usual way, normally Ctrl+Alt+Backspace is for when you need to reset X, eg after editing xorg.conf.  You should have gone to Shutdown>End current session instead.

---

### Post by xyz on 2007-03-15
Thanks for the reply. I'll ckeck my profile.
Will let you know.

That'll teach me to get pissed off! See, I compiled the 2.6.20.1 kernel. Everything went fine except for brightness...to the point that, today, I had to boot the 2.6.17-11-386 kernel just so I coud SEE something on my screen.
The first few days following compilation, the screen brightened up (yes, all by itsefl!) after about 1 hour of use; today nothing after 3h.

So like I said, I got mad and tried to relogin as a sort of stupid desperate gesture! That'll teach me....

---

### Post by xyz on 2007-03-16
OK I found this HowTo: [Mozilla Password Manager Tricks]("http://burntelectrons.org/moz/moz-passwords.html")
Basically it says to go to:
```
~/.mozilla/[Mozilla Profile Name]/[random string].slt/
```
and locate
> a string of numbers for the name, with a .s extension, such as 91453348.s.
containing something like this:
>  [http://bugzilla.mozilla.org](http://bugzilla.mozilla.org)
Bugzilla_login
~ZW1haWxhZHJlc3NAZG9tYWluLmNvbQ==
*Bugzilla_password
~UGFzc3dvcmQ=
Problem is that in
```
root@luser:~/.mozilla/firefox/my_profile# 
```
I have no **[random string].slt/**
Closest thing is: (see **bold**)
> blocklist.xml      defaults.ini      kf.txt           signons2.txt
bookmarkbackups    downloads.rdf     localstore.rdf   signons.txt
bookmarks.bak      extensions        lock             **urlclassifier2.sqlite**
bookmarks.html     extensions.cache  mimeTypes.rdf    user.js
Cache              extensions.ini    prefs.js         **webappsstore.sqlite**
cert8.db           extensions.rdf    ScrapBook        XPC.mfasl
chrome             formhistory.dat   search           xpti.dat
compatibility.ini  history.dat       search.rdf       XUL.mfasl
components.ini     hostperm.1        **search.sqlite**
compreg.dat        install.log       secmod.db
cookies.txt        key3.db           sessionstore.js
and I can't open them. Any help would be appriciated.

---

### Post by xyz on 2007-03-17
In my */home/th/.mozilla/firefox/my_profile/* I've got a:
formhistory.dat

Would I find what I'm looking for in there and how do I open a .dat?
Thnx.

---

### Post by ajgreeny on 2007-03-17
You could open a .dat file using a text editor such as gedit or kate, but I don't think it will help a great deal as it is just gibberish when opened that way I imagine it's an encrypted file for privacy.  Not sure how to help any further, I'm afraid.

---

### Post by xyz on 2007-03-18
Thanks for trying to help.

There are also a couple of "signons.txt" but it doesn't help much.
Here is an example of what one of my passw is supposed to be:
> *pass
MDIEEPgAAAAAAAAAAAAAAAAAAAEwFAYIKoZIhvcNAwcECKd+zrAwoX66BAjK+kqKKTPDtw==
.

---

### Post by xyz on 2007-03-23
So I went into my profile:
```
root@luser:~/.mozilla/firefox/my_profile# 

```
where I found:
>  formhistory.dat
where, I thought, I'd find my lost stuff. But .dat files won't open.
So I used this command line:
```
 rename -v 's/\.dat$/\.txt/' *.dat

```
and got:
> compreg.dat renamed as compreg.txt
formhistory.dat renamed as formhistory.txt
history.dat renamed as history.txt
xpti.dat renamed as xpti.txt

I opened the newly created .txt file:
> // <!-- <mdb:mork:z v="1.4"/> -->
< <(a=c)> // (f=iso-8859-1)
  (80=ns:formhistory:db:row:scope:formhistory:all)
  (81=ns:formhistory:db:table:kind:formhistory)(82=Value)(83=Name)
  (84=ByteOrder)>

<(80=llll)(81=u$00s$00e$00r$00n$00a$00m$00e$00)(82=f$00r$00e$00e$00b$00u$00r$00\
g$00)(83=v$00b$00_$00l$00o$00g$00i$00n$00_$00u$00s$00e$00r$00n$00a$00m$00e$00)
Any ways to 'translate' this gobledegook?
Thanks.

---

