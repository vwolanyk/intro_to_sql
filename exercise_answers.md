SQL INRO to QUERIES

Answers to Exercises

1. HGtoGALAXY robots

SELECT * FROM robots WHERE source='The Hitchhiker''s Guide to the Galaxy';

Result:

Marvin       | The Hitchhiker's Guide to the Galaxy | pessimistic |  3
 Deep Thought | The Hitchhiker's Guide to the Galaxy | thorough    |  7
(2 rows)

2. ANXIETY

SELECT * FROM robots WHERE personality='anxious';

Result:

 name |  source   | personality | id
------+-----------+-------------+----
 C3PO | Star Wars | anxious     |  4
(1 row)

3. NUTTY

SELECT name FROM recipes WHERE nut_free='t'


Result:

                   name                    
-------------------------------------------
 Butternut Squash Bake
 Vegetarian Bibimbap
 French Veggie Loaf
 Quinoa and Black Beans
 Juicy Roasted Chicken
 Garlic Green Beans
 Stout Slow Cooker Corned Beef and Veggies
(7 rows)

4. COUNTING SELECTIONS

SELECT Count(*) FROM recipes WHERE gluten_free = 't' AND vegetarian = 'f';

Result:

 count
-------
     2
(1 row)

5. Animal WITH MAX LEGS

SELECT name, number_of_legs FROM animals WHERE number_of_legs = (SELECT Max(number_of_legs) FROM animals);

Result:

  name   | number_of_legs
---------+----------------
 octopus |              8
(1 row)

6. Board Games

SELECT name, mins_to_play FROM board_games WHERE mins_to_play = intro_to_sql-# (SELECT MIN(mins_to_play) FROM board_games);

Result:

   name   | mins_to_play
----------+--------------
 Sushi Go |           15
 Quixo    |           15
(2 rows)


7. MAX PREP TIME

SELECT name, minutes_required FROM recipes WHERE minutes_required = (SELECT MAX(minutes_required) FROM recipes);

Result:

                   name                    | minutes_required
-------------------------------------------+------------------
 Stout Slow Cooker Corned Beef and Veggies |              390
(1 row)


8. FIND by Wildcard name that starts with "M"

SELECT * FROM robots WHERE name LIKE 'M%';

Result:

      name      |                source                |  personality  | id
----------------+--------------------------------------+---------------+----
 Marvin         | The Hitchhiker's Guide to the Galaxy | pessimistic   |  3
 Mr. Butlertron | Clone High                           | compassionate |  5
(2 rows)

9. NUMBER of Board Games 8 players can play

SELECT COUNT(*) FROM board_games WHERE min_players <=8 AND max_players >=8;
 count

 Result:
-------
     3
(1 row)

10. Swimming AND Egglaying

SELECT * FROM animals WHERE swimming='t' AND egg_laying='t';

Result:

  name   | number_of_legs | flying | swimming | egg_laying | id
---------+----------------+--------+----------+------------+----
 octopus |              8 | f      | t        | t          |  3
 duck    |              2 | t      | t        | t          |  4
(2 rows)


11. Swimming, Egglaying NOT flying

SELECT * FROM animals WHERE flying = 'f' AND swimming='t' AND egg_laying='t';

Result:

  name   | number_of_legs | flying | swimming | egg_laying | id
---------+----------------+--------+----------+------------+----
 octopus |              8 | f      | t        | t          |  3
(1 row)

12. Max Max players

SELECT name, max_players FROM board_games WHERE max_players = (SELECT MAX(max_players) FROM board_games);

Result:

          name          | max_players
------------------------+-------------
 Cards Against Humanity |          30
(1 row)
