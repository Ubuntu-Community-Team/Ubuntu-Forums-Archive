---
title: "[SOLVED] libtommath make isntall wheel group error"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Duffadash on 2007-05-12
Downloaded [libtommath]("http://math.libtomcrypt.com/") as [open c-lit]("http://www.kyz.uklinux.net/convlit.php")needs it.
However, when trying to make install libtommath I get the following error (copied from terminal), the text is quite long though, so you might wonna skip to the bottom:

```
duffadash@Wonderland:~$ cd /home/duffadash/libtommath-0.39
duffadash@Wonderland:~/libtommath-0.39$ ./configure
bash: ./configure: No such file or directory
duffadash@Wonderland:~/libtommath-0.39$ make install
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bncore.o bncore.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_init.o bn_mp_init.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_clear.o bn_mp_clear.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_exch.o bn_mp_exch.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_grow.o bn_mp_grow.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_shrink.o bn_mp_shrink.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_clamp.o bn_mp_clamp.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_zero.o bn_mp_zero.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_set.o bn_mp_set.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_set_int.o bn_mp_set_int.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_init_size.o bn_mp_init_size.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_copy.o bn_mp_copy.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_init_copy.o bn_mp_init_copy.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_abs.o bn_mp_abs.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_neg.o bn_mp_neg.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_cmp_mag.o bn_mp_cmp_mag.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_cmp.o bn_mp_cmp.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_cmp_d.o bn_mp_cmp_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_rshd.o bn_mp_rshd.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_lshd.o bn_mp_lshd.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mod_2d.o bn_mp_mod_2d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_div_2d.o bn_mp_div_2d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mul_2d.o bn_mp_mul_2d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_div_2.o bn_mp_div_2.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mul_2.o bn_mp_mul_2.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_s_mp_add.o bn_s_mp_add.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_s_mp_sub.o bn_s_mp_sub.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_fast_s_mp_mul_digs.o bn_fast_s_mp_mul_digs.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_s_mp_mul_digs.o bn_s_mp_mul_digs.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_fast_s_mp_mul_high_digs.o bn_fast_s_mp_mul_high_digs.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_s_mp_mul_high_digs.o bn_s_mp_mul_high_digs.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_fast_s_mp_sqr.o bn_fast_s_mp_sqr.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_s_mp_sqr.o bn_s_mp_sqr.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_add.o bn_mp_add.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_sub.o bn_mp_sub.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_karatsuba_mul.o bn_mp_karatsuba_mul.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mul.o bn_mp_mul.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_karatsuba_sqr.o bn_mp_karatsuba_sqr.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_sqr.o bn_mp_sqr.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_div.o bn_mp_div.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mod.o bn_mp_mod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_add_d.o bn_mp_add_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_sub_d.o bn_mp_sub_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mul_d.o bn_mp_mul_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_div_d.o bn_mp_div_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mod_d.o bn_mp_mod_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_expt_d.o bn_mp_expt_d.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_addmod.o bn_mp_addmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_submod.o bn_mp_submod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_mulmod.o bn_mp_mulmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_sqrmod.o bn_mp_sqrmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_gcd.o bn_mp_gcd.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_lcm.o bn_mp_lcm.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_fast_mp_invmod.o bn_fast_mp_invmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_invmod.o bn_mp_invmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce.o bn_mp_reduce.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_montgomery_setup.o bn_mp_montgomery_setup.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_fast_mp_montgomery_reduce.o bn_fast_mp_montgomery_reduce.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_montgomery_reduce.o bn_mp_montgomery_reduce.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_exptmod_fast.o bn_mp_exptmod_fast.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_exptmod.o bn_mp_exptmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_2expt.o bn_mp_2expt.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_n_root.o bn_mp_n_root.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_jacobi.o bn_mp_jacobi.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_reverse.o bn_reverse.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_count_bits.o bn_mp_count_bits.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_read_unsigned_bin.o bn_mp_read_unsigned_bin.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_read_signed_bin.o bn_mp_read_signed_bin.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_to_unsigned_bin.o bn_mp_to_unsigned_bin.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_to_signed_bin.o bn_mp_to_signed_bin.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_unsigned_bin_size.o bn_mp_unsigned_bin_size.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_signed_bin_size.o bn_mp_signed_bin_size.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_xor.o bn_mp_xor.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_and.o bn_mp_and.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_or.o bn_mp_or.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_rand.o bn_mp_rand.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_montgomery_calc_normalization.o bn_mp_montgomery_calc_normalization.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_is_divisible.o bn_mp_prime_is_divisible.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_prime_tab.o bn_prime_tab.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_fermat.o bn_mp_prime_fermat.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_miller_rabin.o bn_mp_prime_miller_rabin.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_is_prime.o bn_mp_prime_is_prime.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_next_prime.o bn_mp_prime_next_prime.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_dr_reduce.o bn_mp_dr_reduce.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_dr_is_modulus.o bn_mp_dr_is_modulus.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_dr_setup.o bn_mp_dr_setup.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_setup.o bn_mp_reduce_setup.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_toom_mul.o bn_mp_toom_mul.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_toom_sqr.o bn_mp_toom_sqr.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_div_3.o bn_mp_div_3.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_s_mp_exptmod.o bn_s_mp_exptmod.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_2k.o bn_mp_reduce_2k.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_is_2k.o bn_mp_reduce_is_2k.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_2k_setup.o bn_mp_reduce_2k_setup.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_2k_l.o bn_mp_reduce_2k_l.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_is_2k_l.o bn_mp_reduce_is_2k_l.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_reduce_2k_setup_l.o bn_mp_reduce_2k_setup_l.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_radix_smap.o bn_mp_radix_smap.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_read_radix.o bn_mp_read_radix.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_toradix.o bn_mp_toradix.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_radix_size.o bn_mp_radix_size.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_fread.o bn_mp_fread.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_fwrite.o bn_mp_fwrite.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_cnt_lsb.o bn_mp_cnt_lsb.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_error.o bn_error.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_init_multi.o bn_mp_init_multi.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_clear_multi.o bn_mp_clear_multi.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_exteuclid.o bn_mp_exteuclid.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_toradix_n.o bn_mp_toradix_n.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_random_ex.o bn_mp_prime_random_ex.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_get_int.o bn_mp_get_int.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_sqrt.o bn_mp_sqrt.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_is_square.o bn_mp_is_square.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_init_set.o bn_mp_init_set.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_init_set_int.o bn_mp_init_set_int.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_invmod_slow.o bn_mp_invmod_slow.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_prime_rabin_miller_trials.o bn_mp_prime_rabin_miller_trials.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_to_signed_bin_n.o bn_mp_to_signed_bin_n.c
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bn_mp_to_unsigned_bin_n.o bn_mp_to_unsigned_bin_n.c
ar rv libtommath.a bncore.o bn_mp_init.o bn_mp_clear.o bn_mp_exch.o bn_mp_grow.o bn_mp_shrink.o bn_mp_clamp.o bn_mp_zero.o  bn_mp_set.o bn_mp_set_int.o bn_mp_init_size.o bn_mp_copy.o bn_mp_init_copy.o bn_mp_abs.o bn_mp_neg.o bn_mp_cmp_mag.o bn_mp_cmp.o bn_mp_cmp_d.o bn_mp_rshd.o bn_mp_lshd.o bn_mp_mod_2d.o bn_mp_div_2d.o bn_mp_mul_2d.o bn_mp_div_2.o bn_mp_mul_2.o bn_s_mp_add.o bn_s_mp_sub.o bn_fast_s_mp_mul_digs.o bn_s_mp_mul_digs.o bn_fast_s_mp_mul_high_digs.o bn_s_mp_mul_high_digs.o bn_fast_s_mp_sqr.o bn_s_mp_sqr.o bn_mp_add.o bn_mp_sub.o bn_mp_karatsuba_mul.o bn_mp_mul.o bn_mp_karatsuba_sqr.o bn_mp_sqr.o bn_mp_div.o bn_mp_mod.o bn_mp_add_d.o bn_mp_sub_d.o bn_mp_mul_d.o bn_mp_div_d.o bn_mp_mod_d.o bn_mp_expt_d.o bn_mp_addmod.o bn_mp_submod.o bn_mp_mulmod.o bn_mp_sqrmod.o bn_mp_gcd.o bn_mp_lcm.o bn_fast_mp_invmod.o bn_mp_invmod.o bn_mp_reduce.o bn_mp_montgomery_setup.o bn_fast_mp_montgomery_reduce.o bn_mp_montgomery_reduce.o bn_mp_exptmod_fast.o bn_mp_exptmod.o bn_mp_2expt.o bn_mp_n_root.o bn_mp_jacobi.o bn_reverse.o bn_mp_count_bits.o bn_mp_read_unsigned_bin.o bn_mp_read_signed_bin.o bn_mp_to_unsigned_bin.o bn_mp_to_signed_bin.o bn_mp_unsigned_bin_size.o bn_mp_signed_bin_size.o bn_mp_xor.o bn_mp_and.o bn_mp_or.o bn_mp_rand.o bn_mp_montgomery_calc_normalization.o bn_mp_prime_is_divisible.o bn_prime_tab.o bn_mp_prime_fermat.o bn_mp_prime_miller_rabin.o bn_mp_prime_is_prime.o bn_mp_prime_next_prime.o bn_mp_dr_reduce.o bn_mp_dr_is_modulus.o bn_mp_dr_setup.o bn_mp_reduce_setup.o bn_mp_toom_mul.o bn_mp_toom_sqr.o bn_mp_div_3.o bn_s_mp_exptmod.o bn_mp_reduce_2k.o bn_mp_reduce_is_2k.o bn_mp_reduce_2k_setup.o bn_mp_reduce_2k_l.o bn_mp_reduce_is_2k_l.o bn_mp_reduce_2k_setup_l.o bn_mp_radix_smap.o bn_mp_read_radix.o bn_mp_toradix.o bn_mp_radix_size.o bn_mp_fread.o bn_mp_fwrite.o bn_mp_cnt_lsb.o bn_error.o bn_mp_init_multi.o bn_mp_clear_multi.o bn_mp_exteuclid.o bn_mp_toradix_n.o bn_mp_prime_random_ex.o bn_mp_get_int.o bn_mp_sqrt.o bn_mp_is_square.o bn_mp_init_set.o bn_mp_init_set_int.o bn_mp_invmod_slow.o bn_mp_prime_rabin_miller_trials.o bn_mp_to_signed_bin_n.o bn_mp_to_unsigned_bin_n.o
ar: creating libtommath.a
a - bncore.o
a - bn_mp_init.o
a - bn_mp_clear.o
a - bn_mp_exch.o
a - bn_mp_grow.o
a - bn_mp_shrink.o
a - bn_mp_clamp.o
a - bn_mp_zero.o
a - bn_mp_set.o
a - bn_mp_set_int.o
a - bn_mp_init_size.o
a - bn_mp_copy.o
a - bn_mp_init_copy.o
a - bn_mp_abs.o
a - bn_mp_neg.o
a - bn_mp_cmp_mag.o
a - bn_mp_cmp.o
a - bn_mp_cmp_d.o
a - bn_mp_rshd.o
a - bn_mp_lshd.o
a - bn_mp_mod_2d.o
a - bn_mp_div_2d.o
a - bn_mp_mul_2d.o
a - bn_mp_div_2.o
a - bn_mp_mul_2.o
a - bn_s_mp_add.o
a - bn_s_mp_sub.o
a - bn_fast_s_mp_mul_digs.o
a - bn_s_mp_mul_digs.o
a - bn_fast_s_mp_mul_high_digs.o
a - bn_s_mp_mul_high_digs.o
a - bn_fast_s_mp_sqr.o
a - bn_s_mp_sqr.o
a - bn_mp_add.o
a - bn_mp_sub.o
a - bn_mp_karatsuba_mul.o
a - bn_mp_mul.o
a - bn_mp_karatsuba_sqr.o
a - bn_mp_sqr.o
a - bn_mp_div.o
a - bn_mp_mod.o
a - bn_mp_add_d.o
a - bn_mp_sub_d.o
a - bn_mp_mul_d.o
a - bn_mp_div_d.o
a - bn_mp_mod_d.o
a - bn_mp_expt_d.o
a - bn_mp_addmod.o
a - bn_mp_submod.o
a - bn_mp_mulmod.o
a - bn_mp_sqrmod.o
a - bn_mp_gcd.o
a - bn_mp_lcm.o
a - bn_fast_mp_invmod.o
a - bn_mp_invmod.o
a - bn_mp_reduce.o
a - bn_mp_montgomery_setup.o
a - bn_fast_mp_montgomery_reduce.o
a - bn_mp_montgomery_reduce.o
a - bn_mp_exptmod_fast.o
a - bn_mp_exptmod.o
a - bn_mp_2expt.o
a - bn_mp_n_root.o
a - bn_mp_jacobi.o
a - bn_reverse.o
a - bn_mp_count_bits.o
a - bn_mp_read_unsigned_bin.o
a - bn_mp_read_signed_bin.o
a - bn_mp_to_unsigned_bin.o
a - bn_mp_to_signed_bin.o
a - bn_mp_unsigned_bin_size.o
a - bn_mp_signed_bin_size.o
a - bn_mp_xor.o
a - bn_mp_and.o
a - bn_mp_or.o
a - bn_mp_rand.o
a - bn_mp_montgomery_calc_normalization.o
a - bn_mp_prime_is_divisible.o
a - bn_prime_tab.o
a - bn_mp_prime_fermat.o
a - bn_mp_prime_miller_rabin.o
a - bn_mp_prime_is_prime.o
a - bn_mp_prime_next_prime.o
a - bn_mp_dr_reduce.o
a - bn_mp_dr_is_modulus.o
a - bn_mp_dr_setup.o
a - bn_mp_reduce_setup.o
a - bn_mp_toom_mul.o
a - bn_mp_toom_sqr.o
a - bn_mp_div_3.o
a - bn_s_mp_exptmod.o
a - bn_mp_reduce_2k.o
a - bn_mp_reduce_is_2k.o
a - bn_mp_reduce_2k_setup.o
a - bn_mp_reduce_2k_l.o
a - bn_mp_reduce_is_2k_l.o
a - bn_mp_reduce_2k_setup_l.o
a - bn_mp_radix_smap.o
a - bn_mp_read_radix.o
a - bn_mp_toradix.o
a - bn_mp_radix_size.o
a - bn_mp_fread.o
a - bn_mp_fwrite.o
a - bn_mp_cnt_lsb.o
a - bn_error.o
a - bn_mp_init_multi.o
a - bn_mp_clear_multi.o
a - bn_mp_exteuclid.o
a - bn_mp_toradix_n.o
a - bn_mp_prime_random_ex.o
a - bn_mp_get_int.o
a - bn_mp_sqrt.o
a - bn_mp_is_square.o
a - bn_mp_init_set.o
a - bn_mp_init_set_int.o
a - bn_mp_invmod_slow.o
a - bn_mp_prime_rabin_miller_trials.o
a - bn_mp_to_signed_bin_n.o
a - bn_mp_to_unsigned_bin_n.o
ranlib libtommath.a
install -d -g wheel -o root /usr/lib
install: invalid group `wheel'
make: *** [install] Error 1

```

Anybody able to helve me solve this?

---

### Post by kebes on 2007-05-12
Alot of software installs require you to be "superuser" in order to perform the installation. Installing it as the admin user would probably fix it:
```

sudo make install

```
(then enter your password)

Of course, it goes without saying that you should not install software using "sudo" unless you trust the source of the software.


Hope that helps.

---

### Post by Duffadash on 2007-05-12
Tried that already. No effect, doesn't even ask for a password actually:

```
duffadash@Wonderland:~$ cd /home/duffadash/libtommath-0.39
duffadash@Wonderland:~/libtommath-0.39$ make clean
rm -f *.bat *.pdf *.o *.a *.obj *.lib *.exe *.dll etclib/*.o demo/demo.o test ltmtest mpitest mtest/mtest mtest/mtest.exe \
        *.idx *.toc *.log *.aux *.dvi *.lof *.ind *.ilg *.ps *.log *.s mpi.c *.da *.dyn *.dpi tommath.tex `find . -type f | grep [~] | xargs` *.lo *.la
rm -rf .libs
cd etc ; MAKE=make make clean
make[1]: Entering directory `/home/duffadash/libtommath-0.39/etc'
rm -f *.log *.o *.obj *.exe pprime tune mersenne drprime tune86 tune86l mont 2kprime pprime.dat \
         *.da *.dyn *.dpi *~
make[1]: Leaving directory `/home/duffadash/libtommath-0.39/etc'
cd pics ; MAKE=make make clean
make[1]: Entering directory `/home/duffadash/libtommath-0.39/pics'
rm -rf *.ps *.pdf .xvpics
make[1]: Leaving directory `/home/duffadash/libtommath-0.39/pics'
duffadash@Wonderland:~/libtommath-0.39$ sudo make install
cc -I./ -Wall -W -Wshadow -Wsign-compare -O3 -funroll-loops -fomit-frame-pointer   -c -o bncore.o bncore.c
[..]
a - bn_mp_to_unsigned_bin_n.o
ranlib libtommath.a
install -d -g wheel -o root /usr/lib
install: invalid group `wheel'
make: *** [install] Error 1
duffadash@Wonderland:~/libtommath-0.39$
```

---

### Post by Duffadash on 2007-05-13
Nobody able to help me?
(sorry 'bout the double post)

---

### Post by kebes on 2007-05-13
> **Duffadash said:**
> install -d -g wheel -o root /usr/lib
install: invalid group `wheel'
make: *** [install] Error 1


The "wheel" group is part of the unix admin system. It controls who has access to become superuser using the "su" command. However Ubuntu doesn't really use "su" and instead uses "sudo" so the wheel group doesn't actually exist. So I can think of three ways to fix your current situation:

1. Create the wheel group (this might be done automatically if you activate the root account, which is by default turned off on Ubuntu).I don't recommend this because it will change all kinds of other things about your system.

2. Do this:
```

sudo -s
make install

```
Basically this puts you into a root shell using the sudo command. Inside that environment, the install command might work. Then again, maybe it won't, since the wheel group still doesn't exist.

3. Go into the install code for the package, and find the line where it says:
```

install -d -g wheel -o root /usr/lib
```
And change it to be:
```

install -d -g **root** -o root /usr/lib
```

I think this would fix the problem, but then again it might have unintended consequences. For instance the software might have built-in assumptions about how it was installed. Anyways, looking at the source code for libtomcrypt, I think the change you have to make is to go into the file "makefile" and alter line 32:
```

#install as this user
ifndef INSTALL_GROUP
   GROUP=wheel
else
   GROUP=$(INSTALL_GROUP)
endif

```

Change the line from "GROUP=wheel" to "GROUP=root", save the file, and then re-run the "sudo make install" command.

Hope that works.

---

### Post by Duffadash on 2007-05-13
ahh, it seems to have worked. Thanks alot!

---

