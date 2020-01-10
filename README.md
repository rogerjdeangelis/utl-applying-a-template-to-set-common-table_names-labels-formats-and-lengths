# utl-applying-a-template-to-set-common-table_names-labels-formats-and-lengths
Applying a template to set common table names labels formats and lengths  
    Applying a template to set common table names labels formats and lengths                                                           
                                                                                                                                       
    github                                                                                                                             
    https://tinyurl.com/wqmx47j                                                                                                        
    https://github.com/rogerjdeangelis/utl-applying-a-template-to-set-common-table_names-labels-formats-and-lengths                    
                                                                                                                                       
    *_                   _                                                                                                             
    (_)_ __  _ __  _   _| |_                                                                                                           
    | | '_ \| '_ \| | | | __|                                                                                                          
    | | | | | |_) | |_| | |_                                                                                                           
    |_|_| |_| .__/ \__,_|\__|                                                                                                          
            |_|                                                                                                                        
    ;                                                                                                                                  
                                                                                                                                       
                                                                                                                                       
    data Template;                                                                                                                     
                                                                                                                                       
     attrib                                                                                                                            
       CLAIM_NO          length=$20  format=$20.        label="CLAIM_NO        "                                                       
       ADMIT_DT          length=8    format=datetime20. label="ADMIT_DT        "                                                       
       ID_MEDICAID       length=$12  format=$12.        label="ID_MEDICAID     "                                                       
       DTE_BIRTH         length=8    format=datetime20. label="DTE_BIRTH       "                                                       
       CDE_SEX           length=$1   format=$1.         label="CDE_SEX         "                                                       
       ID_PROVIDER       length=$9   format=$9.         label="ID_PROVIDER     "                                                       
       CDE_ADMIT_TYPE    length=$1   format=$1.         label="CDE_ADMIT_TYPE  "                                                       
       CDE_ADMIT_SOURCE  length=$20  format=$20.        label="CDE_ADMIT_SOURCE"                                                       
    ;                                                                                                                                  
                                                                                                                                       
    run;quit;                                                                                                                          
                                                                                                                                       
    * remove the observation from the template;                                                                                        
    data Template ;                                                                                                                    
         modify Template                                                                                                               
                Template ;                                                                                                             
         by CLAIM_NO;                                                                                                                  
         remove;                                                                                                                       
    run;quit;                                                                                                                          
                                                                                                                                       
    * insert this data into template renaming and chaging all attributes;                                                              
    data OLD;                                                                                                                          
                                                                                                                                       
       CLAIM_NO          = "A6753";                                                                                                    
       admit_dt          = datetime();                                                                                                 
       ID_MEDICAID       = "AKSAA";                                                                                                    
       DTE_BIRTH         = datetime()-24*60*60;                                                                                        
       CDE_SEX           = "M";                                                                                                        
       ID_PROVIDER       = "98317A";                                                                                                   
       CDE_ADMIT_TYPE    = "R";                                                                                                        
       CDE_ADMIT_SOURCE  = "HOSPICE";                                                                                                  
                                                                                                                                       
      label                                                                                                                            
       CLAIM_NO         =   "CLM     "                                                                                                 
       admit_dt         =   "ADM     "                                                                                                 
       ID_MEDICAID      =   "MEDICAID"                                                                                                 
       DTE_BIRTH        =   "BIRTH   "                                                                                                 
       CDE_SEX          =   "GENDER  "                                                                                                 
       ID_PROVIDER      =   "PTVDR   "                                                                                                 
       CDE_ADMIT_TYPE   =   "ATYPE   "                                                                                                 
       CDE_ADMIT_SOURCE =   "SOURCE  "                                                                                                 
     ;                                                                                                                                 
    run;quit;                                                                                                                          
                                                                                                                                       
    WORL.OLD                                                                                                                           
                                                                                                                                       
               Variables in Creation Order                                                                                             
                                                                                                                                       
    #    Variable            Type    Len    Label                                                                                      
                                                                                                                                       
    1    CLAIM_NO            Char      5    CLM                                                                                        
    2    ADMIT_DT            Num       8    ADM                                                                                        
    3    ID_MEDICAID         Char      5    MEDICAID                                                                                   
    4    DTE_BIRTH           Num       8    BIRTH                                                                                      
    5    CDE_SEX             Char      1    GENDER                                                                                     
    6    ID_PROVIDER         Char      6    PTVDR                                                                                      
    7    CDE_ADMIT_TYPE      Char      1    ATYPE                                                                                      
    8    CDE_ADMIT_SOURCE    Char      7    SOURCE                                                                                     
                                                                                                                                       
    *            _               _                                                                                                     
      ___  _   _| |_ _ __  _   _| |_                                                                                                   
     / _ \| | | | __| '_ \| | | | __|                                                                                                  
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                   
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                  
                    |_|                                                                                                                
    ;                                                                                                                                  
                                                                                                                                       
    Names and attributes are those of the template;                                                                                    
                                                                                                                                       
                                                                                                                                       
                          Variables in Creation Order                                                                                  
                                                                                                                                       
    #    Variable            Type    Len    Format         Label                                                                       
                                                                                                                                       
    1    CLAIM_NO            Char     20    $20.           CLAIM_NO                                                                    
    2    ADMIT_DT            Num       8    DATETIME20.    ADMIT_DT                                                                    
    3    ID_MEDICAID         Char     12    $12.           ID_MEDICAID                                                                 
    4    DTE_BIRTH           Num       8    DATETIME20.    DTE_BIRTH                                                                   
    5    CDE_SEX             Char      1    $1.            CDE_SEX                                                                     
    6    ID_PROVIDER         Char      9    $9.            ID_PROVIDER     OLD                                                         
    7    CDE_ADMIT_TYPE      Char      1    $1.            CDE_ADMIT_TYPE                                                              
    8    CDE_ADMIT_SOURCE    Char     20    $20.           CDE_ADMIT_SOURCEMAPPING                                                     
                                                                                                                                       
                                                                                                                                       
    WORK.WANT total obs=2                                                                                                              
                                                                                                                                       
                                                                                                      CDE_ADMIT_    CDE_ADMIT_         
     CLAIM_NO              ADMIT_DT    ID_MEDICAID             DTE_BIRTH    CDE_SEX    ID_PROVIDER       TYPE         SOURCE           
                                                                                                                                       
      A6753      10JAN2020:15:13:31       AKSAA       09JAN2020:15:13:31       M         98317A           R          HOSPICE           
                                                                                                                                       
    *          _       _   _                                                                                                           
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                                
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                               
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                              
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                              
                                                                                                                                       
    ;                                                                                                                                  
                                                                                                                                       
    proc sql;                                                                                                                          
                                                                                                                                       
      create                                                                                                                           
         table want as                                                                                                                 
      select                                                                                                                           
         *                                                                                                                             
      from                                                                                                                             
         template                                                                                                                      
                                                                                                                                       
      union                                                                                                                            
                                                                                                                                       
      select                                                                                                                           
         *                                                                                                                             
      from                                                                                                                             
         old                                                                                                                           
                                                                                                                                       
    ;quit;                                                                                                                             
                                                                                                                                       
                                                                                                                                       
                                                                                                                                       
