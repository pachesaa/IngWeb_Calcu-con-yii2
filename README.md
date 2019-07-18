# CRUD Con Yii2
Tutorial para la creación de un CRUD en yii2(PHP) calculadora

# Pre - Requisitos 📋
Descargar Yii con xampp
- https://www.yiiframework.com/download
- https://www.apachefriends.org/es/download.html

# Desarrollo 🛠️
- Creación de una aplicacion web Calculadora
- Crear una nueva aplicación con Yii2 (Framework) con el nombre de Basic descargado anteriormente en yii, despues cambiar a nombre Calcu, copiarlo y pegarlo en htdocs.
- Descargar cualquier editor de texto, Sublime 3, Visual Code ETC.

# Desarrollo en Visual Code 🛠️

- Creacion en yii Generation para modelo,controlador y vista.
  - En ProgresoController
    - Funcion Index
  
          public function actionIndex()
            {
                $searchModel = new ProgresoSearch();
                $dataProvider = $searchModel->search(Yii::$app->request->queryParams);
                $datos = $dataProvider->query->all();
                $nuevos = [];

                foreach($datos as $key => $item){
                    $aux =  new \stdClass();
                    $aux->id = $item->id;
                    $aux->nombre = $item->nombre;
                    $aux->progreso1 = $item->progreso1;
                    $aux->progreso2 = $item->progreso2;
                    $aux->progreso3 = $this->calcular($item->progreso1,$item->progreso2);
                    $nuevos[$item->id]=$aux;

                }


                return $this->render('index', [
                    'searchModel' => $searchModel,
                    'dataProvider' => $dataProvider,
                    'datos'=>$nuevos,

                ]);
            }
          
    - Funcion Calcular  
          
          private function calcular($nota1,$nota2){

          $calcu1=(($nota1*0.25)+($nota2*0.35));
          $calcu=(6-$calcu1)/0.40;

          return $calcu;
          }
          
          
# Guardar y ejecutar el proyecto(ejecutar en Xampp control panel Apache y MySQL)
 - http://localhost/calcu/web/index.php

          
      
