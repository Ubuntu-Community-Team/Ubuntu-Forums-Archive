---
title: "Re: Unable to change my default program"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Gryphin on 2007-01-20
I hope someone reads this tough topic states it's resolved.

I am unable to change my default applications no matter what I do. I always get response:

Unable to add application to database.
(this is not exact information cause my Ubuntu is in Polish and I translated the way i think it should go in English).

I asked in few other forums with no response.
What can I do?

---

### Post by aysiu on 2007-01-20
Make sure you have full ownership of your home directory: ```
sudo chown -R gryphin:gryphin /home/gryphin
```

---

