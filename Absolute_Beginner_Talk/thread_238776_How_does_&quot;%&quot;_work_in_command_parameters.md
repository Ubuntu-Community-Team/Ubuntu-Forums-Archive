---
title: "How does &quot;%&quot; work in command parameters?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by klytu on 2006-08-18
I have noticed many apps that are invoked in a gnome application launcher with %something parameters. Examples:

```
sound-juicer -d %d
totem %m
firefox %u
```

I have also come across these mysterious (to me :-)) %something parameters in various configuration files. I haven't been able to find any explanation of what they do or why they are used. 

Can anyone shed some light on this? Not just the specific examples above (though that would be useful, too), but is there a general reference?

---

### Post by huygens on 2006-08-18
Hi,

Some of those characters are part of the [Freedesktop specification]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html#exec-variables"). Gnome is following this specification for [its Launchers]("http://www.gnome.org/learn/users-guide/latest/launchers.html#launchers-properties").

However, this specification should be followed only by Desktop software. I do not know of which configuration files you were refering, but they could have other meaning...

Huygens

---

### Post by klytu on 2006-08-18
> **huygens said:**
> Hi,

Some of those characters are part of the [Freedesktop specification]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-0.9.4.html#exec-variables"). Gnome is following this specification for [its Launchers]("http://www.gnome.org/learn/users-guide/latest/launchers.html#launchers-properties").

However, this specification should be followed only by Desktop software. I do not know of which configuration files you were refering, but they could have other meaning...

Huygens

Thanks! The links you posted are very helpful. I'll post some examples from configuration files later when I get back home from work. It may be that the  files I have come across are indeed only for Desktop software, but I don't remember offhand.

---

