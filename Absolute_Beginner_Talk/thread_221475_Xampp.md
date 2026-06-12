---
title: "Xampp"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-23
can ubuntu use XAMPP?

---

### Post by rowanparker on 2006-07-23
You could just check [here]("https://help.ubuntu.com/community/ApacheMySQLPHP"). It's easier to do than XAMPP.

Rowan.

---

### Post by jlhughes on 2006-07-24
> **rowanparker said:**
> It's easier to do than XAMPP.

I use the Xampp (Lampp) put out by Apachefriends.org. I tried to use the individual programs available through apt-get under the assumption that Ubuntu's automatic upgrading would be easier. But the lack of a unified configuration script (which comes with Xampp -- Lampp) make the individual route a lot more work. In addition, Apachefriends.org's package comes with Apache 2.2 and PHP 5.x. There's extra configuration required in Ubuntu if you want the native Debian packages to work.

Now, I'm speaking as a novice Linux user. There may be some reason to adhere to Debian's structure for the basic LAMP components, instead of putting all of the binaries in the /opt/lampp directory. But when it comes to out-of-the-box-it-just-works functionality, I believe Apachefriends.org's package is a much better deal.  In fact, I think Ubuntu should adobt Apachefriends.org's package for that reason.

---

### Post by rowanparker on 2006-07-24
Well, each to their own, I found seperate one's easier.

But in answer to your question: Yes Ubuntu can use XAMPP.

Rowan.

---

### Post by superjet on 2006-07-25
Hello there,
 Please keep in mind that Xampp is not to be used on the net or in production enviroments. They even say on the site that is if for development only.

 Security is very lax on this product.

Jamie

---

