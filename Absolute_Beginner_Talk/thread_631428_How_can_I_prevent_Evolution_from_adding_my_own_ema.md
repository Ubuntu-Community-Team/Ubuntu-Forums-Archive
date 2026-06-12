---
title: "How can I prevent Evolution from adding my own email address when I reply?"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by soichih on 2007-12-04
When I reply emails on Evolution, Evolution will automatically add my own email address in CC section. Is there way to disable this behavior?

---

### Post by kelbizzle on 2007-12-04
Goto Edit > Preferences, CLick  on the account then click edit on the right.  Now click the defaults tab.  Under where it says composing messages do you see your email address in the "Always cc to" field ?

---

### Post by soichih on 2007-12-04
No, both "Always carbon-copy" and "Always blind carbon-copy" are both not checked and text fields are empty.

Also, my email address is added to CC when I do "reply-all" instead of just "reply".. sorry for miss-description.

---

### Post by kelbizzle on 2007-12-04
Oh ok I just tried to reply all to a group email I received I couldn't reproduce your issue. In the "TO:" Field of the incoming email Is your email listed in the group twice?

---

### Post by soichih on 2007-12-07
I found out what the issue was..

In my preference, I had my email address listed as "soichih@foo.com", but in the Outlook exchange server, it was listed as "soichi.hayashi@foo.com". So, when I push Reply All, Evolution thought that [email]soichi.hayashi@foo.com[/email] that is translated by the outlook server was a different email address from [email]soichih@foo.com[/email] and adding it to my CC box.

I have reconfigured my preference to have [email]soichi.hayashi@foo.com[/email] as the email address and not it is not adding it to my CC!

Is it possible for Evolution to check both expanded and non-expanded email address and make sure that it will not add either address to CC when doing Reply-All?

---

