#### Overview


**Simona Halep - short ranking history and number of titles by year**


**2012** - First Top 50 season; runner-up at Brussels; semifinalist at Fès; quarterfinalist twice

**2013** - Near-Top 10 season (finishing No.11); went 7-9 in first nine WTA main draws, reaching 3 round once and 2 round five times but falling 1 round three times and in qualifying once; went 43-8 in next 14 WTA main draws, highlighted by first **six WTA titles** at Nürnberg, 's-Hertogenbosch, Budapest, New Haven, Moscow and Sofia; also semifinalist at Rome and quarterfinalist at Cincinnati; made Top 20 debut on August 26 (after New Haven; rose from No.23 to No.19) and peaked at No.11 on November 4 year-end rankings

**2014** - First Top 10 season (finishing No.3); won **two WTA titles** at Doha and Bucharest; runner-up three times at Madrid, Roland Garros and WTA Finals; semifinalist twice at Indian Wells and Wimbledon; quarterfinalist three times at Australian Open, Cincinnati and Beijing;having started the year at No.11, made Top 10 debut on January 27, Top 5 debut on March 17 and set career-high No.2 on August 11 (highest-ranked Romanian in WTA history)

**2015** - Best season to date (finishing No.2); won **three WTA titles** at Shenzhen, Dubai and Indian Wells; runner-up twice at Toronto and Cincinnati; semifinalist four times at Miami, Stuttgart, Rome and US Open; quarterfinalist three times at Australian Open, Birmingham and Guangzhou

**2016** - Current ranking 5; won **two WTA titles** at Madrid and Bucharest; semifinalist at Sydney; quarterfinalist at Indian Wells, Miami and Wimbledon

The figures presented above show a good trend. In 2013 at 23 years old she won her first six titles, 2 on clay, 1 on grass and 2 on hard courts. Halep became the only player of the year to win titles on clay, grass, hard, and indoor courts, as well as the second most successful player behind Serena Williams in terms of number of titles won. 2014 and 2015 were transitional years in which she tried to get more used with the pressure of being a top player. The beginning of 2016 saw a Simona Halep struggling with injuries and a loss of form. Her first title of the year came in May in Madrid.

The present analysis looks at the numbers on her serve, the winners and the unforced errors, the strategy that she is following, the way her game developed through the last four years.

#### Datasets

Csv files used from:

https://github.com/JeffSackmann/tennis_MatchChartingProject

1. Forced_errors
2. Overview
3. return_depth
4. return_outcomes
5. servebasics
6. servedirection
7. shotdirection
8. surfaces
9. win_lose
10. games

![Fig.1](https://github.com/silvelie/Data-Science/blob/master/raw%20data%20files.png)


Initial format of the data - variables:

##### Overview1 

1. match_id (including date, gender, tournament, round, player 1 and player 2 separated by "-") - first variable in every file
2. player
3. set
4. serve_pts
5. aces
6. dfs
7. first_in
8. first_won
9. second_in
10. second_won
11. bk_pts
12. bp_saved
13. return_pts
14. return_pts_won
15. winners
16. winners_fh
17. winners_bh
18. unforced
19. unforced_fh
20. unforced_bh

##### Forced_errors

21. row
22. pts
23. won
24. forced

##### return_depth

25. returnable
26. shallow
27. deep
28. very_deep
29. unforced
30. err_net
31. err_deep
32. err_wide
33. err_wide_deep

##### return_outcomes

34. return_pts
35. return_pts_won
36. returnable_won
37. in_play
38. in_play_won
39. return_winners
40. total_shots

##### servebasics

41. pts_on_serve
42. pts_on_serve_won
43. unret
44. forced_err
45. pts_won_lte_3_shots
46. wide
47. body
48. t

##### servedirection

49. deuce_wide
50. deuce_middle
51. deuce_t
52. ad_wide
53. ad_middle
54. ad_t
55. err_net
56. err_wide
57. err_deep
58. err_wide_deep
59. err_foot
60. err_unknown

##### shotdirection

61. crosscourt
62. down_middle
63. down_the_line
64. inside_out
65. inside_in

##### surfaces
##### win_lose
##### games

#### Data wrangling

Using the dplyr and tidyr packages, the following wrangling was done to the datasets:

* Separate match_id into 6 different columns: Date, gender, tournament, round, player 1 and player 2
* Subset only data that contains Simona Halep as player 1 or player 2
* Transform variable Date in 3 columns : Year, Month, Day
* Combine dataset overview_total( from the initial Overview1 subsetting by Simona Halep and the total number of data per match) with win_lose(contains 2 columns win or lose and number of sets played), surface(contains Tournament and Surface) and games(contains number of games played) - cbind() and left_join() used. 
* Combine overview_total with all the other datasets: forced_errors_total, return_depth_total, return_outcomes_total, servebasics_total, servedirection_total, shotdirection_total.

#### Data analysis

The analysis covers 152 matches over a span of four years from May 2013 to June 2016. From the 152 matches, 114 were wins (75%) and 38 were losses(25%).

A preliminary analysis shows:
+ the wins and losses by Tournament, Surface and Year
+ the average number of winners (20 winners is the mean on clay, followed very closely by the mean on grass and hard courts) and unforced errors ( the mean between 20 and 28, on grass it tends to be smaller).

![Fig.2](https://github.com/silvelie/Data-Science/blob/master/Win_lose_by_tournament_surface_year.png)

![Fig.3](https://github.com/silvelie/Data-Science/blob/master/winners_by_surface.png)

![Fig.4](https://github.com/silvelie/Data-Science/blob/master/unforced_by_surface.png)
