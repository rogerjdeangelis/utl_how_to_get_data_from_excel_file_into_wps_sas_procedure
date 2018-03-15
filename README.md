# utl_how_to_get_data_from_excel_file_into_wps_sas_procedure
How to get data from excel file into wps sas procedure like optmodel. 
    How to get data from excel file into wps or sas procedure like optmodel

    github
    https://tinyurl.com/y9nhlvyh
    https://github.com/rogerjdeangelis/utl_how_to_get_data_from_excel_file_into_wps_sas_procedure

    No need to run proc import/export (soon to be deprecated? I hope).

    Is excel the tail wagging the dog(SAS/WPS)?

    Excel may be considered a small player but the structure of the input
    data and the knowledge(excel users) around it impact the future of SAS/WPS.


    SAS forum
    https://tinyurl.com/y9nhlvyh
    https://communities.sas.com/t5/Base-SAS-Programming/How-to-get-data-from-e-g-an-Excel-file-into-a-vector/m-p/445749


    INPUT  EXCEL Sheet or named range INVCOUNT
    ==========================================

      d:/xls/have.xlsx

      +-------------------------+
      |     A      |    B       |
      +-------------------------+
    1 |   ITEM     | INVCOUNT   |
      +------------+------------+
    2 |  table     |  100       |
      +------------+------------+
    3 |  sofa      |  250       |
      +------------+------------+
    4 |  chair     |   80       |
      +------------+------------+

     [INVCOUNT]

     libname xel "d:/xls/have.xlsx";


    PROCESS  (All the code)
    =======================

     We only need to pint to the excel workbook.

     proc optmodel;
     set<string> Items;
     number invcount{Items};
     read data xel.have into Items=[item] invcount;
     print invcount;
     quit;


    OUTPUT
    =====

    The OPTMODEL Procedure

    [1]      INVCOUNT

    chair          80
    sofa          250
    table         100

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    libname xel "d:/xls";
    data xel.have;
      input item$ invcount;
    cards4;
    table 100
    sofa 250
    chair 80
    ;;;;
    run;quit;



    proc optmodel;
    set<string> Items;
    number invcount{Items};
    read data invdata into Items=[item] invcount;
    print invcount;

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;
    proc optmodel;
    set<string> Items;
    number invcount{Items};
    read data xel.have into Items=[item] invcount;
    print invcount;
    quit;
    libname xel clear;

