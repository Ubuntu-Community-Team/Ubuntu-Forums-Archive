---
title: "Java Problem"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by gth835x on 2007-05-15
Can someone tell me what this means


java.lang.NoSuchMethodError: com.sun.tools.javac.util.Options.put(Ljava/lang/String;Ljava/lang/String;)V

---

### Post by nereid on 2007-05-15
This error just says that this function *put* ain't available with two string arguments.

---

### Post by Zootropo on 2007-05-15
That's strange because from what I see that class extends HashMap: [http://www.krugle.com/examples/p-RgJDnwsJbLEW6Sge/Options.java](http://www.krugle.com/examples/p-RgJDnwsJbLEW6Sge/Options.java)

which of course has a put(Object, Object) method

---

### Post by nereid on 2007-05-17
Yeah, a hashmap has the put option defined for that. Seems a little strange to me. Which version of java are you using? sun-1.5?

---

