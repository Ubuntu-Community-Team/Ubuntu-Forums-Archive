---
title: "after hrs of debugging, im looking for answers. problem is mysql.sock?! Ruby Rails..."
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by bbqbaker on 2006-02-26
i bought a book about ruby on rails and going through the whole project phase. well i am now stuck on creating the scaffold. here is the error:

koloa@ubuntu:/var/www/depot$ ruby script/generate scaffold Product Admin
      exists  app/controllers/
      exists  app/helpers/
      exists  app/views/admin
      exists  test/functional/
  dependency  model
      exists    app/models/
      exists    test/unit/
      exists    test/fixtures/
   identical    app/models/product.rb
   identical    test/unit/product_test.rb
   identical    test/fixtures/products.yml
No such file or directory - /tmp/mysql.sock



////////////////////////////////////////////////////////

now i have been searching the forums and google but getting even more confused. what is the difference between mysql.sock and mysqld.sock? 

does mysql port number have to be the same that my RoR site is on?

---

### Post by suRoot on 2006-02-26
Is mySQL running?

---

### Post by bbqbaker on 2006-02-26
yes. i mean i believe so. in the begining i  type sudo mysqld.

---

