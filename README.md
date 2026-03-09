El proyecto del grupo 5 fue estructurado en dos partes de la siguiente manera:

* PARTE 1
    En la  primera etapa se intenta identificar patrones inusuales en el comportamiento del trafico de red, mediente los siguientes pasos:
    - Se utiliza un dataset (.csv) que contiene regitros de tráfico de red donde se incluye las columnas de session_id, tamaño de paquete de red (network_packet_size), protocolo usado (protocol_type), intentos de login (login_attempts), duracion de la sesion (session_duration), encripcion empleada (encryption_used), reputacion de la ip (ip_reputation_score), intentos fallidos de login (failed_logins), tipo de navegador (browser_type), horario de acceso inusual (unusual_time_access), si se cataloga como un ataque (attack_detected).
    - Se determina los navegadores que se han usado en las sesiones y cual ha sido el mas empleado para partir de ahi el analisis, sin descartar aquellos navegadores mencionados como desconocidos, ya que pueden ser una brecha de seguridad alta.
    - Se realiza la limpieza de datos, eliminando aquellos nulos que no aporten informacion, y se reemplaza aquellos valores inconsistentes con nulos para hacer una segunda limpieza.
    - Se hace una comparacion y correlacion del promedio de duracion de las sesiones que se han hecho en los diferentes navegadores, esto ante una posible vulnerabilidad de credenciales y acceso a cuentas o posibles intentos de fuerza bruta. (Una sesión muy larga podría indicar acceso no autorizado o persistencia por parte de un atacante.)
    - Posteriormente se analizan los intentos fallidos de login en los datos atipicos de duracion de sesion en los navegadores.  (Un alto número de inicios de sesión fallidos indican robo de credenciales o ataques de diccionario. Muchos intentos fallidos seguidos de un inicio de sesión exitoso podrían sugerir que una cuenta estaba comprometida.)
    - Se revisa la reputacion de la IP de esos datos atipicos, para poder concluir si efectivamente el comportamiento corresponde a un ataque. (En la puntuación de IP de 0 a 1, los valores más altos indican actividad sospechosa. Las direcciones IP asociadas con botnets, spam o ataques anteriores tienden a tener puntuaciones más altas)
    - La clasificación binaria de ( attack_detected): 1 significa que se detectó un ataque, 0 significa actividad normal. El conjunto de datos es útil para el aprendizaje automático supervisado , donde un modelo aprende de patrones de ataque etiquetados.

* PARTE 2
    Corresponde al entranamiento y evaluacion del modelo.
    - Se divide los registros en dos partes, una para entrenamiento y otra para evuluarlo.
    - Se usa machine learning para poder ingresar primero en la etapa de prediccion y posteriormente evaluacion.
    - Clasificación binaria de ( attack_detected): 1significa que se detectó un ataque, 0significa actividad normal. El conjunto de datos es útil para el aprendizaje automático supervisado , donde un modelo aprende de patrones de ataque etiquetados.
    - Se despliega la matriz de consufusion para para analizar si el modelo esta prediciendo efectivamente teniendo como base de efectividad el campo de  (attack_detected).


