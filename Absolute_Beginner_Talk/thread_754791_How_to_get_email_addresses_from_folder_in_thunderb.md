---
title: "How to get email addresses from folder in thunderbird?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-04-14
Hello,

I have a folder in Thunderbird with many messages. Now I want to extract all the email addresses from the people that sent me emails and save them somehow.

Is there any way to do this?

---

### Post by hyper_ch on 2008-04-14
(1) mark all messages in the folder

(2) right-click and choose to export selected messages in a file

(3) you could try to filter out all email addresses from there...

---

### Post by sillyxone on 2008-04-14
I think Thunderbird stores the mail folders as ASCII files, so you can run grep on those files to extract email addresses. You can go into ~/.mozilla-thunderbird to find your Thunderbird profile. For example, I was able to get all email addresses from my "Sent" folder (executed from my ~/.mozilla-thunderbird/g5v257l3.default/Mail/Local Folders)

```
 grep -o -E '<[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}>' Sent
```

However, it also grab the message-id addresses created by email servers such as '8903a.09983@yahoo.com', so probably you want to restrict it to From|To|CC|BCC only:

```
 grep '^\(From\|To\|Cc\|CC\Bcc\|BCC\):' Sent | grep -o -E '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}'
```

to get a list of unique addresses, pipe the result into "sort" and "uniq" to remove duplicates:

```
grep '^\(From\|To\|Cc\|CC\Bcc\|BCC\):' Sent | grep -o -E '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}' | sort -f | uniq -i
```

However, it will only grabs the addresses, and probably is only useful if you are a spammer. I think you can play around with REGEX to extract the associated names as well.

---

### Post by kramer65 on 2008-04-14
@ sillyxone

Thank you for all that code. It works miraculously!

Now I got only one problem. When I do this it gives a list. But the terminal window doesn't show such a long list. So I can look back (by scrolling up) but I can't see all the email addresses because at one point I can't scroll up anymore..

How can I maybe save all of them in a file or something? Or maybe there is another way?

---

### Post by aeiah on 2008-04-14
```
grep '^\(From\|To\|Cc\|CC\Bcc\|BCC\):' Sent | grep -o -E '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}' | sort -r | uniq -i > file.list
```

the bit on the end should pipe it to a file called file.list

---

### Post by kramer65 on 2008-04-14
That solves everything!

Thank you so much!

---

### Post by forrestcupp on 2008-04-14
That's a pretty cool way to do it, but there may be an easier way.  [addressContext](https://addons.mozilla.org/en-US/thunderbird/addon/152) is a great addon for Thunderbird that allows you to just select as many emails as you want and add either the senders or recipients as new cards in your contacts.  You just select them, then right click and addressContext has a menu entry with options of what to do with the addresses.

---

### Post by hyper_ch on 2008-04-14
forrestcupp: that's way too simple *g*

---

