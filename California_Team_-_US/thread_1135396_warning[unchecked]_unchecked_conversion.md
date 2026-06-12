---
title: "warning:[unchecked] unchecked conversion"
date: 2009-04-24
forum: California Team - US
---

### Post by prmdshinde on 2009-04-24
Hi all,

I am getting following warning :

warning:[unchecked] unchecked conversion
[javac]found:java.util.List
[javac] required:java.util.List<edu.fullerton.cs476s09.espressobar.jpa.espressobar_milk>
return query.getResultList();


What may the problem and probable solution.
I am using following code:
 
@Stateless
@Remote(Order.class)
//@EntityListeners(MyListener.class)
public class OrderBean implements Order { 
    /**
     * The entity manager object, injected by the container
     */
    @PersistenceContext
    private EntityManager manager;
  public List<espressobar_milk> listMilk() {
        Query query = manager.createQuery("SELECT m FROM espressobar_milk m");
        return query.getResultList();
    }...
.....
..}

Thanks in advance for any suggestion.

---

